<template>
  <v-dialog v-model="show" persistent max-width="38vw">
    <div class="d-flex pa-5">
      <div class="form-container">
        <v-form ref="form">
          <v-card>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="12" md="6">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="this.firstName"
                      outlined
                      label="First name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="12" md="6">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="this.lastName"
                      outlined
                      label="Last name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="this.companyName"
                      outlined
                      label="Company Name"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required]"
                      v-model="this.jobTitle"
                      outlined
                      label="Job Title"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      :rules="[rules.required, rules.email]"
                      v-model="this.email"
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
                class="my-5 mx-auto white--text btn"
                large
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
          contain
          width="4vw"
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
        this.signUp();
      } else {
        return;
      }
    },
    signUp() {
      const data = {
        first_name: this.firstName,
        last_name: this.lastName,
        company_name: this.companyName,
        email: this.email,
      };
      console.log(data);
      this.$emit("close");
    },
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
.exit {
  width: 45px;
}
.exit:hover {
  cursor: pointer;
}

.parent-container {
  display: flex;
  flex-wrap: nowrap;
}

.form-container {
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
</style>
