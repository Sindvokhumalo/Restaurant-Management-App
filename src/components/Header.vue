<template>
    <div class="nav">
    <router-link to="/">HOME</router-link>
    <router-link to="/add-info">ADD DATA</router-link>
  
    <router-link  to="" @click="Logout">LOGOUT</router-link>
</div>
</template>

<script>

export default{
    name : 'Header',
    methods: {
        Logout(){
                    localStorage.clear();// clear the localstorage info
                    this.$router.push({name:'Login'});// relocate to login page
        }
    }
}
</script>

<style>
.nav {
    background-color: #333;
    overflow: hidden;
}

.nav a {
    float: left;
    color: aliceblue;
    padding: 14px 14px;
    text-decoration: none;
    text-align: center;
    font-size: 17px;
    margin-right: 5px;
}
.nav a:hover{
   background: white;
   color: black;
   
}

</style>

