<template>
  <router-view/>
</template>

<script>

export default {
  name: 'App',
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
 /* margin-top: 60px;*/
}
body{
  padding: 0;
  margin: 0;
}
.logo {
    width: 100px;
}

.register input, .login input, .add input, .update input{
    width: 300px;
    height: 35px;
    display: block;
    padding-left: 20px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid #2c3e50;
    border-radius: 10px 2px;
}
.register button, .login button, .add button, .update button{
    width: 325px;
    height: 30px;
    cursor: pointer;
    background-color: #2c3e50;
    color: white;
    border-radius: 10px;
}
</style>
