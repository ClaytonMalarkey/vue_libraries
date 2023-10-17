<template>
    <div>
      <h1>All Users</h1>
      <div v-for="user in users" :key="user.id">
        <p>{{ user.first_name }} {{ user.last_name }}</p>
        <p>{{ user.email }}</p>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        users: [],
      };
    },
    mounted() {
      this.fetchUsers();
    },
    methods: {
      async fetchUsers() {
        try {
          const response = await axios.get('https://reqres.in/api/users');
          this.users = response.data.data;
        } catch (error) {
          console.error('Error fetching users:', error);
        }
      },
    },
  };
  </script>
  