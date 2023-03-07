<template>
    <Header />
    <h1>Hello {{ name }}, Welcome to home page </h1>

    <table border="1">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Address</td>
            <td>Actions</td>
        </tr>

        <tr v-for="item in restuarant" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contacts }}</td>
            <td>{{ item.address }}</td>
            <td>
                <router-link :to="'/update-info/' + item.id">Update</router-link>
                <button @click="deleteRecord(item.id)">Delete</button>
            </td>
        </tr>

    </table>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios';

export default {
    name: 'Home',

    components: {
        Header
    },
    methods: {
        async deleteRecord(id) {
            //  console.warn(id);
            let result = await axios.delete("http://localhost:3000/restuarant/" + id);

        //    console.warn(result);

            if (result.status == 200) {
                        
                        alert('Record Deleted !!')
                        this.loadData()
            }


        },
        async loadData() {
            let user = localStorage.getItem('user-info');
            this.name = JSON.parse(user).name;
            if (!user) {
                this.$router.push({ name: 'SignUp' })

            }

            let result = await axios.get("http://localhost:3000/restuarant");
            //console.warn(result);
            this.restuarant = result.data;
        }
    },

    data() {
        return {
            name: '',
            restuarant: []
        }
    },

    async mounted() {// check info on locl storge then redirects---lifecycle method clled when pge is loded
        this.loadData()
    }



}
</script>

<style>
td {
    height: 50px;
    width: 200px;
}

table {
    margin-left: auto;
    margin-right: auto;
}
</style>