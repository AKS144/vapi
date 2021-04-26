<template>
    <div>
        <h1>Post</h1>
        <form @submit="submitData" method="post">
            <input type="text" name="title" v-model="post.title"/><br><br>
            <input type="text" name="author" v-model="post.author"/><br><br>
            <button type="submit">Post</button>
        </form>
    </div>
</template>

<script> 
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)//binded with Vue vue-axios and axios

export default {
    name: 'post',
    data()
    {
        return {
            post:{
                title:null,
                author:null,
            }
        }
    },
    methods:
    {
        submitData(e)
        {
            this.axios.post('http://localhost:3000/posts',this.post).then((result)=>{  //this.axios because axios part of vue now after binding
                console.warn("result",result)//then promise for the callback executed with parameter
            })//this used when binding, 2 parameter url in postman and data to be send
            //console.warn(this.post)  //for listing all data
            e.preventDefault();//to prevent default function when form refresh 
        }
    }
}
</script>