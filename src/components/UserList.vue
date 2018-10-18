<template>
  <div class="home">
    <h1>This is a user list</h1>
    <ul v-if="users">
      <li v-for="user in users">
        <p>{{ user.name }}</p>
        <p>{{ user.email }}</p>
      </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="error of errors">
        {{error.message}}
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios';

  export default{
    data(){
      return {
        users:[],
        errors:[]
      }
    },
    created() {
      axios.get('http://127.0.0.1:8000/api/users')
        .then(response => {
            this.users = response.data
        }) .catch (error => {
          this.errors.push(error)
        })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
