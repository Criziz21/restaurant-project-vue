<template>
  <img class="logo" src="../assets/logo.jpg" />
  <h1>Sign in</h1>
  <div class="login">
    <input type="text" v-model="email" placeholder="Enter Email">
    <input type="password" v-model="password" placeholder="Enter Password">
    <button v-on:click="signIn">Sign up</button>
    <p>
      <router-link to="/sign-up">Sign Up</router-link>
    </p>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name:'SignIn',
  data() {
    return {
      email:'',
      password:''
    }
  },
  methods: {
    async signIn() {
      let result = await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`);
      if(result.status == 200 && (result.data.length > 0)) {
        localStorage.setItem("user-info", JSON.stringify(result.data[0]));
        this.$router.push({name:'HomePage'})
      }
    }
  },
  mounted() {
    let user = localStorage.getItem('user-info')
    if(user) {
      this.$router.push({name:'HomePage'});
    }
  }
}
</script>

<style>
</style>
