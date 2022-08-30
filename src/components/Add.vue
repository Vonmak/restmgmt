<template>
  <Header/>
  <h1>Hello, user. This is your add page</h1>
  <form action="" class="add">
    <input type="text" placeholder="Enter Name" name="name" v-model="Restaraunt.name">
    <input type="tel" placeholder="Enter Contact" name="contact" v-model="Restaraunt.contact">
    <input type="text" placeholder="Enter Address" name="address" v-model="Restaraunt.address">
    <button type="button" v-on:click="addRes">Add New Res</button>
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
    }
};
</script>
<style scoped></style>
