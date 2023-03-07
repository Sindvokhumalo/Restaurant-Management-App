<template>
    <Header/>
<h1>Update Data</h1>
<form class="update">
        <input type="text" name="name" placeholder="Enter Name" v-model="restuarant.name"/>
        <input type="text" name="address" placeholder="Enter Address" v-model="restuarant.address"  />
        <input type="text" name="contacts" placeholder="Enter Contact" v-model="restuarant.contacts" />
        <button type="button" @click="UpdateRestuarant">Update Restuarant</button>
    </form>

</template>

<script>
import Header from './Header.vue'
import axios from 'axios';


export default {
    name: 'Update',
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
       async UpdateRestuarant()
       {    
                //console.warn(this.restuarant);
              let result = await axios.put("http://localhost:3000/restuarant/"+this.$route.params.id, {//update data
               name:this.restuarant.name,
               address:this.restuarant.address,
               contacts:this.restuarant.contacts
               
            });
         //   console.warn(result);
         if(result.status==200)
         {
            this.$router.push({name:'Home'})//redirects  to home

         }

        }
    },
   async mounted(){// check info on locl storge then redirects---lifecycle method clled when pge is loded
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
            
            }
             //   console.warn(this.$route.params.id); fetch data from url
             let result = await axios.get("http://localhost:3000/restuarant/"+this.$route.params.id)
            // console.warn(result.data);
             this.restuarant=result.data;
    }
}

</script>