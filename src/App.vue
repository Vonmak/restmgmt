<template>
  <router-view/>
</template>

<script>

export default {
  name: 'App',
  components: {
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  margin: 0;
  padding: 0;

}
.logo {
  width: 100px;
}
.head{
  color: skyblue;
}
.register input, .login input, .add input{
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid skyblue;
  border-radius: 5px;
}
.register button, .login button, .add button{
  width: 200px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: #fff;
  cursor: pointer;
  border-radius: 5px;
}
.register button:hover, .login button:hover, .add button:hover{
  color: skyblue;
  background: #fff;
}
p a{
  text-decoration: none;
  color: skyblue;
}
.btn{
  margin: 3px;
}
</style>
