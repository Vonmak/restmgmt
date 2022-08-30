<template>
  <Header/>
  <h1>Hello, {{name}}.</h1>
  <h4>Add New Restaraunt</h4>
  <form action="" class="add">
    <input type="text" placeholder="Enter Name" name="name" v-model="Restaraunt.name">
    <input type="tel" placeholder="Enter Contact" name="contact" v-model="Restaraunt.contact">
    <input type="text" placeholder="Enter Address" name="address" v-model="Restaraunt.address">
    <button type="button" v-on:click="addRes">Submit</button>
  </form>
</template>
<script>
import Header from './Header.vue';
import axios from "axios";
export default {
    name: "Add",
    components: { Header },
    data(){
      return{
        name:'',
        Restaraunt:{
          name:'',
          contact:'',
          address:'',
        }
      }
    },
    methods:{
      async addRes(){
        let result = await axios.post('http://localhost:3000/restaraunt',{
          name:this.Restaraunt.name,
          address:this.Restaraunt.address,
          contact:this.Restaraunt.contact
        })
        console.log(result)
        if (result.status == 201) {
        this.$router.push({ name: "Home" });
      }
      }
    },
    mounted(){
      let user = localStorage.getItem("user_info");
      if (!user) {
        this.$router.push({ name: "Login" });
      }
      this.name = JSON.parse(user).name;
    }
};
</script>
<style scoped></style>
