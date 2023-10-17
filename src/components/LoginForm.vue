<template>
    <div>
      <h2>Login Form</h2>
      <form @submit.prevent="login">
        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email" required />
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required />
        </div>
        <button type="submit">LOGIN</button>
      </form>
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        email: "",
        password: "",
        errorMessage: "",
      };
    },
    methods: {
      async login() {
        try {
          const response = await axios.post("https://reqres.in/api/login", {
            email: this.email,
            password: this.password,
          });
          if (response.data.token) {
            document.cookie = `token=${response.data.token}`;
            this.errorMessage = "";
          } else {
            this.errorMessage = "Login failed. Please check your credentials.";
          }
        } catch (error) {
          console.error("Login error:", error);
          this.errorMessage = "An error occurred during login.";
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .error {
    color: red;
  }
  </style>
  