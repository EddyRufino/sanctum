<template>
  <div>
    <form @submit.prevent="login">
      <input v-model="form.email" type="email" placeholder="Email..."/> <br>
      <input v-model="form.password" type="password" placeholder="password..." /> <br>
      
      <button>Login</button>

    </form>
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
          email: 'eddyjaair@gmail.com',
          password: 'password'
        }
      }
    },

    methods: {
      async login() {
        await this.$store.dispatch("login", this.form);
        return this.$router.push("/");
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>