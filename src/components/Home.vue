<template>
  <Header />

  <h1>Hello, {{ name }}. Welcome!!</h1>
  <h4>Table consisting of Restaraunts</h4>
  <table class="table" border="1">
    <thead>
      <tr>
        <td>#</td>
        <td>Name:</td>
        <td>Contact:</td>
        <td>Address:</td>
        <td>Actions:</td>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in restaraunt" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
        <td>
          <router-link :to="'/update/' + item.id" class="btn btn-primary">Update</router-link>
          <button v-on:click="deleRes(item.id)" class="btn btn-danger">Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Home",
  components: { Header },
  methods: {
    async deleRes(id) {
      let result = await axios.delete("http://localhost:3000/restaraunt/" + id);
      if(result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user_info");
      if (!user) {
        this.$router.push({ name: "Login" });
      }
      this.name = JSON.parse(user).name;
      let result = await axios.get("http://localhost:3000/restaraunt");
      this.restaraunt = result.data;
    },
  },
  async mounted() {
    this.loadData();
  },
  data() {
    return {
      name: "",
      restaraunt: [],
    };
  },
};
</script>
<style scoped>
</style>
