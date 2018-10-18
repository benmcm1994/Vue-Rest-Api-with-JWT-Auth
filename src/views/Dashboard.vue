<template>
  <div class="dashboard">
    <h1>Dashboard page</h1>
    <router-link :to="{ name: 'logout' }">Logout</router-link>
        <ul>
        <li v-for="user in users">
        <p>{{ user.name }}</p>
      </li>
        </ul>
  </div>
</template>

<script>
import axios from "axios";
import store from '../store'

export default {
  data(){
    return {
      users: []
    }
  },
  mounted(){
    axios.get('http://127.0.0.1:8000/api/users', {
      headers: {
        Authorization: 'Bearer ' + localStorage.getItem('token')
      }
    })
    .then(response => {
      this.users = response.data
      console.log(data)
    }) .catch (error => {

    })
  }
}
</script>
