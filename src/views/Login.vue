<template>
  <!-- <div>
    <form @submit.prevent="login">
      <input v-model="form.email" type="email" placeholder="Email..." /> <br />
      <input
        v-model="form.password"
        type="password"
        placeholder="password..."
      />
      <br />

      <button>Login</button>
    </form>
  </div> -->
<div id="app">
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
                <v-toolbar-title>Login form</v-toolbar-title>
                <v-spacer />

              </v-toolbar>
              <v-card-text>
                <v-form @submit.prevent="login">
                  <v-text-field
                    label="Email"
                    v-model="form.email"
                    prepend-icon="person"
                    type="text"
                  />

                  <v-text-field
                    id="password"
                    label="Password"
                    v-model="form.password"
                    prepend-icon="lock"
                    type="password"
                  />
                  <v-card-actions>
                    <v-spacer />
                    <v-btn @click="login" color="primary">Login</v-btn>
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
// import axios from 'axios';
// axios.defaults.withCredentials = true;
// axios.defaults.baseURL = 'http://localhost:8000';

export default {
  data() {
    return {
      form: {
        email: "eddyjaair@gmail.com",
        password: "password"
      }
    };
  },

  methods: {
    async login() {
      await this.$store.dispatch("login", this.form);
      return this.$router.push("/");
    }
  }
};
</script>

<style lang="scss" scoped></style>
