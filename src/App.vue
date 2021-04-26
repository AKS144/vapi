<template>
  <div id="app">
    <h1>API</h1>
    <post />
    <users />
   </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import post from './components/post.vue'
import users from './components/users.vue'

export default {
  name: 'App',
  components: {
    //HelloWorld,
    post,
    users
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
  margin-top: 60px;
}
</style>
