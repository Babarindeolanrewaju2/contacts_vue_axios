<template>
<div id=#app>
    <div v-for="user in users" v-bind:key="user.id">
        <h1>Name: {{ user.name }}</h1>
        <p>Email: {{ user.email }}</p>
        <p>Username: {{ user.username }}</p>
        <p>phone: {{ user.phone }}</p>
        <p>Address: {{ user.address.street }}</p>
        <p>Address: {{ user.address.zipcode }}</p>
    </div>
    <button @click="fetchUsers">Click me!</button>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'app',
    data() {
        return {
            users: []
        }
    },
    methods: {
        fetchUsers: function () {
            const baseURI = 'https://jsonplaceholder.typicode.com/users'
            axios.get(baseURI)
                .then((result) => {
                    this.users = result.data
                    console.log(result.data)
                })
        }
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    width: 640px;
    height: 300px;
    margin: 0 auto;
    color: #2c3e50;
    margin-top: 60px;
}

button {
    background-color: #4CAF50;
    /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
}
</style>
