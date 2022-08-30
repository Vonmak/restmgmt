<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Restaraunt</router-link>
    <a href="" v-on:click="logout">Logout</a>
  </div>
</template>
<script>
export default {
  name: "Header",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style scoped>
.nav {
  background: #333;
  overflow: hidden;
}
.nav a {
  color: #ffffff;
  padding: 14px 16px;
  text-align: center;
  font-size: 17px;
  text-decoration: none;
  margin-right: 5px;

  float: left;
}
.nav a:hover {
  color: #333;
  background: aliceblue;
  border-radius: 5px;
}
</style>
