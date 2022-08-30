<template>
  <Header />
  <h1>Hello, {{name}}.</h1>
  <h4>Update Restaraunt</h4> 
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
    <button type="button" v-on:click="upRes">Submit</button>
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
      name:'',
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
    if (!user) {
      this.$router.push({ name: "Login" });
    }
    this.name=JSON.parse(user).name;
    const result = await axios.get(
      "http://localhost:3000/restaraunt/" + this.$route.params.id
    );
    console.log(result);
    this.Restaraunt = result.data;
  },
};
</script>
<style scoped></style>
