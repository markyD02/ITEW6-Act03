<template>
    <div class="login">
      <h1>Log in</h1>
      <form @submit.prevent="login">
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" required>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required>
        <button type="submit">Login</button>
      </form>
      <p v-if="error" class="error">{{ error }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        error: ''
      };
    },
    methods: {
            login() {
          setTimeout(() => {
              if (this.username !== '' && this.password !== '') {
                  localStorage.setItem('token', '12345'); 
                  this.$router.push({ name: 'home' }); 
                  this.error = ''; 
              } else {
                  this.error = 'Invalid username or password';
              }
          }, 500);
      }
    }
  };
  </script>  
  
  <style scoped>
  .login {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccbfbf;
    border-radius: 8px;
    background-color: #d2c7c7;
  }
  
  form {
    display: flex;
    flex-direction: column;
  }
  
  label {
    margin-bottom: 5px;
  }
  
  input {
    margin-bottom: 10px;
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  
  button {
    padding: 8px;
    border-radius: 4px;
    border: none;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
  }
  
  .error {
    color: red;
  }
  </style>
  