<template>
    <img alt="Vue logo" class='logo' src="../assets/logo.png">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Enter name" v-model="name">
        <input type="email" placeholder="Email address" v-model="email">
        <input type="password" placeholder="Password" v-model="password">
        <button v-on:click="signup">Sign Up</button>
    </div>
</template>
<script>
    import axios from 'axios'
   export default {
    name: 'SignUp',
    data(){
        return{
            name:'',
            email:'',
            password:'',
        }
    },
    methods: {
        async signup(){
            let result = await axios.post('http://localhost:3000/users/',{
                name: this.name,
                email:this.email,
                password:this.password
            })
            console.log(result)
            if(result.status == 201){
                alert('Successful Registration')
                localStorage.setItem('user_info',JSON.stringify(result.data))
            }
        }
    }
   }
</script>
<style scoped>
.logo{
    width: 100px;
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid skyblue;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background: skyblue;
    color: #fff;
    cursor: pointer;
}
</style>