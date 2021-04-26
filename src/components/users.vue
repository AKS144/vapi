<template>
<div>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>Email</td>           
            <td>Action</td>
        </tr>
        <tr v-for="user in users" v-bind:key="user.id">
            <td>{{user.title}}</td>
            <td>{{user.author}}</td>           
            <td><button v-on:click="deleteUser(user.id)">Delete</button></td>
        </tr>
    </table>
</div>    
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'//package
Vue.use(VueAxios, axios)//binding of axios

export default {
    name:'users',
    data(){
        return {users:null}
    },
    methods:
    {
        getUsers()
        {
           this.axios.get('http://localhost:3000/posts').then((result)=>{
                console.warn(result)
                this.users=result.data //data if from data function
            })            
        },
        deleteUser(id)
        {
            this.axios.delete('http://localhost:3000/posts/'+id).then((result)=>{
                console.warn(result)
                //this.users=result.data
                this.getUsers()
            })
        }
    },
    mounted()
    {
        this.getUsers() //in mounted axios can be called but we took other function because it has to be used 2 times
    }
}
</script>