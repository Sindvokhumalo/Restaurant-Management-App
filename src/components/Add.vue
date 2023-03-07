<template>
    <Header/>
    <h1>Add Data</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restuarant.name"/>
        <input type="text" name="address" placeholder="Enter Address"  v-model="restuarant.address"/>
        <input type="text" name="contacts" placeholder="Enter Contact"  v-model="restuarant.contacts"/>
        <button type="button" @click="addRestuarant">Add New Restuarant</button>
    </form>
    
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';


export default {
    name: 'Add',
    components: {
        Header
    },

    data(){
        return{
                restuarant: {
                    name: '',
                    address: '',
                    contacts: ''
                }
        }
    },

    methods:{
       async addRestuarant(){
          //  console.warn(this.restuarant);
            let result = await axios.post("http://localhost:3000/restuarant", {
               name:this.restuarant.name,
               address:this.restuarant.address,
               contacts:this.restuarant.contacts
               
            });
         //   console.warn(result);
         if(result.status==201)
         {
            this.$router.push({name:'Home'})//redirects  to home

         }
           
        }
    },
    mounted(){// check info on locl storge then redirects---lifecycle method clled when pge is loded
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
            
            }

    }
}

</script>