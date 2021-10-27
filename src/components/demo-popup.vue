<template>
  <v-dialog v-model="show" persistent :fullscreen="isMobile">
    <div class="d-flex pa-5 dialog">
      <div class="form-container">
        <v-form ref="form">
          <v-card>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="12" md="6">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="firstName"
                      outlined
                      label="First name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="12" md="6">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="lastName"
                      outlined
                      label="Last name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="companyName"
                      outlined
                      label="Company Name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="jobTitle"
                      outlined
                      label="Job Title"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required, rules.email]"
                      v-model="email"
                      label="Business Email Address"
                      outlined
                      required
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-btn
                v-if="isMobile"
                class="my-5 mx-auto black--text btn"
                x-large
                width="10vw"
                color="#DCDCDC"
                @click="$emit('close')"
                depressed
              >
                Back
              </v-btn>
              <v-btn
                class="my-5 mx-auto white--text btn"
                x-large
                width="10vw"
                color="#7776bc"
                @click="validate"
                depressed
              >
                Send
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-form>
      </div>
      <div class="exit-btn-container">
        <v-img
          v-if="!isMobile"
          contain
          class="exit mt-n2"
          :src="require('@/assets/close.png')"
          @click="$emit('close')"
        >
        </v-img>
      </div>
    </div>
  </v-dialog>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    firstName: "",
    lastName: "",
    companyName: "",
    jobTitle: "",
    email: "",
    rules: {
      required: (value) => !!value || "Required.",
      email: (value) => {
        const pattern =
          /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return pattern.test(value) || "Invalid e-mail.";
      },
    },
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.inquire();
      } else {
        return;
      }
    },
    inquire() {
      let bodydata = new FormData();

      bodydata.append('name', this.firstName + " " + this.lastName)
      bodydata.append('company_name', this.companyName)
      bodydata.append('job_title', this.jobTitle)
      bodydata.append('email', this.email)

      axios({
        method: "post",
        url: "zwell-prod.ap-southeast-1.elasticbeanstalk.com",
        data: bodydata,
      })

      this.$emit("close");
    },
  },
  created() {
    this.isMobile = window.innerWidth <= 896 ? true : false;
  },
  props: {
    show: {
      type: Boolean,
    },
  },
};
</script>

<style lang="scss" scoped>
::v-deep .v-dialog {
  box-shadow: none;
}

.dialog {
  justify-content: center;
}

.exit {
  width: 4.2rem;
}
.exit:hover {
  cursor: pointer;
}

.parent-container {
  display: flex;
  flex-wrap: nowrap;
}

.form-container {
  max-width: 38vw;
  align-self: flex-start;
  justify-self: flex-start;
}

.exit-btn-container {
  align-self: flex-start;
  justify-self: flex-end;
}

.btn {
  text-transform: none;
}

@media (max-width: 1200px) {
  .form-container {
    max-width: 60vw;
  }
}

@media (max-width: 600px) {
  .exit {
    width: 2.8rem;
  }
  .form-container {
    max-width: 100vw;
  }
}
</style>
