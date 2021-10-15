<template>
  <v-row justify="center">
    <div class="parent-container">
      <div class="form-container">
        <v-dialog v-model="show" persistent max-width="38vw">
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
                  class="mx-auto white--text"
                  large
                  width="10vw"
                  color="#7776bc"
                  @click="validate"
                >
                  Send
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-form>
        </v-dialog>
      </div>
      <div class="exit-btn-container">
        <v-img
          class="exit"
          :src="require('@/assets/close.png')"
          @click="$emit('close')"
        >
        </v-img>
      </div>
    </div>
  </v-row>
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
  background: red;
}
</style>
