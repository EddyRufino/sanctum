<template>
  <div>
    <form @submit.prevent="register">
      <input v-model="form.name" type="text"> <br>
      <input v-model="form.email" type="email"> <br>
      <input v-model="form.password" type="password"> <br>
      <input v-model="form.password_confirmation" type="password"> <br>

      <button>Register</button>
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
          name: 'Ana Vierita',
          email: 'anavierita@gmail.com',
          password: 'password',
          password_confirmation: 'password'
        }
      }
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
    },
  }
</script>

<style lang="scss" scoped>

</style>