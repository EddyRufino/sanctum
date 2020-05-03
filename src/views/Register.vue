<template>
  <div id="app">
    <!-- <form @submit.prevent="register">
      <input v-model="form.name" type="text" /> <br />
      <input v-model="form.email" type="email" /> <br />
      <input v-model="form.password" type="password" /> <br />
      <input v-model="form.password_confirmation" type="password" /> <br />

      <button>Register</button>
    </form> -->
  <v-app id="inspire">
    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
                <v-toolbar-title>Register form</v-toolbar-title>
                <v-spacer />

              </v-toolbar>
              <v-card-text>
                <v-form @submit.prevent="register">
                  <v-text-field
                    label="Name"
                    v-model="form.name"
                    prepend-icon="person"
                    type="text"
                  />

                  <v-text-field
                    label="Email"
                    v-model="form.email"
                    prepend-icon="person"
                    type="email"
                  />

                  <v-text-field
                    id="password"
                    label="Password"
                    v-model="form.password"
                    prepend-icon="lock"
                    type="password"
                  />

                  <v-text-field
                    id="password"
                    label="Password"
                    v-model="form.password_confirmation"
                    prepend-icon="lock"
                    type="password"
                  />
                  <v-card-actions>
                    <v-spacer />
                    <v-btn type="submit" @click="register" color="primary">Register</v-btn>
                  </v-card-actions>
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
  </div>
</template>

<script>
import axios from 'axios';
axios.defaults.withCredentials = true;
axios.defaults.baseURL = 'http://localhost:8000';

export default {
  data() {
    return {
      form: {
        name: "Ana Vieris",
        email: "anavieris@gmail.com",
        password: "password",
        password_confirmation: "password"
      }
    };
  },
  methods: {
    async register() {
      await this.$store.dispatch("register", this.form);
      return this.$router.push("/");

      // axios.get('http://localhost:8000/sanctum/csrf-cookie').then(() => {
      //   axios.post("http://localhost:8000/register", this.form)
      //         .then(res => {
      //           console.log(res.data);
      //           return this.$router.push("/");
      //         })
      //         .catch(err => {
      //           console.log(err);
      //         });
      // });
    }
  }
};
</script>

<style lang="scss" scoped></style>
