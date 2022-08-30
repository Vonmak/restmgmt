<template>
  <img alt="Vue logo" class="logo" src="../assets/logo.png" />
  <h2 class="head">Sign Up</h2>
  <div class="register">
    <input type="text" placeholder="Enter name" v-model="name" />
    <input type="email" placeholder="Email address" v-model="email" />
    <input type="password" placeholder="Password" v-model="password" />
    <button v-on:click="signup">Sign Up</button>
    <p>Have an Account?
      <router-link to="/login">Log In Here</router-link>
    </p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signup() {
      let result = await axios.post("http://localhost:3000/users/", {
        name: this.name,
        email: this.email,
        password: this.password,
      });
      console.log(result);
      if (result.status == 201) {
        localStorage.setItem("user_info", JSON.stringify(result.data));
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
<style scoped>

</style>
