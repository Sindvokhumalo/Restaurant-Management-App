<template>
    <img class="logo" src="../assets/res-logo.png" alt=""/>
   
    <h1>SignUp</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name"/>
        <input type="text" v-model="email" placeholder="Enter Email"/>
        <input type="password" v-model="password" placeholder="Enter Pssword"/>
        <button @click="signUp">Sign UP</button>
        <p>
          Already a Member? <router-link to="/login">Go to Login</router-link>
        </p>

    </div>

</template>

<script>
import axios from 'axios'
export default {
    name : 'SignUp',
    data(){
        return{
            name: '',
            email: '',
            password: ''
        }
    },
    methods: {
       async signUp(){

            let result = await axios.post("http://localhost:3000/users",{
                name:this.name, 
                email:this.email, 
                password:this.password
            });

            console.log(result);
            if(result.status ==201){
                localStorage.setItem("user-info",JSON.stringify(result.data))//sve on locl storge
                this.$router.push({name:'Home'})
            }
        }
    },
    mounted(){// check info on locl storge then redirects
        let user = localStorage.getItem('user-info');
        if(user){
            this.$router.push({name:'Home'})

            }

    }
}
</script>

<style>

</style>