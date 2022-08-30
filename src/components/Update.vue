<template>
  <Header />
  <h1>Hello, user. This is your update page</h1>
  <form action="" class="add">
    <input
      type="text"
      placeholder="Enter Name"
      name="name"
      v-model="Restaraunt.name"
    />
    <input
      type="tel"
      placeholder="Enter Contact"
      name="contact"
      v-model="Restaraunt.contact"
    />
    <input
      type="text"
      placeholder="Enter Address"
      name="address"
      v-model="Restaraunt.address"
    />
    <button type="button" v-on:click="upRes">Update Res</button>
  </form>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Update",
  components: { Header },
  data() {
    return {
      Restaraunt: {
        name: "",
        contact: "",
        address: "",
      },
    };
  },
  methods: {
    async upRes() {
      const result = await axios.put(
        "http://localhost:3000/restaraunt/" + this.$route.params.id,
        {
          name: this.Restaraunt.name,
          address: this.Restaraunt.address,
          contact: this.Restaraunt.contact,
        }
      );
      if (result.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  async mounted() {
    let user = localStorage.getItem("user_info");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "Login" });
    }
    const result = await axios.get(
      "http://localhost:3000/restaraunt/" + this.$route.params.id
    );
    console.log(result);
    this.Restaraunt = result.data;
  },
};
</script>
<style scoped></style>
