<template>
  <img alt="Vue logo" class="logo" src="../assets/logo.png" />
  <h2 class="head">Login</h2>
  <div class="login">
    <input type="email" placeholder="Email address" v-model="email" />
    <input type="password" placeholder="Password" v-model="password" />
    <button v-on:click="login">Sign Up</button>
    <p>Don't have an Account?
      <router-link to="/signup">Sign Up Here</router-link>
    </p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let result = await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`);
      console.log(result);
      if(result.status == 200 && result.data.length>0) {
        localStorage.setItem("user_info", JSON.stringify(result.data[0]));
        this.$router.push({ name: "Home" });
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user_info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style scoped></style>
