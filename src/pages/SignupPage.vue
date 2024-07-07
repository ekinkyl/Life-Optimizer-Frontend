<template>
    <div id="app">
      <nav class="navbar">
        <div class="menu">
          <a href="#">Help</a>
          <router-link to="/login">Log In</router-link>
        </div>
      </nav>
      <div class="register-container">
        <router-link to="/" class="logo-link"> 
          <div class="register-logo">
            <img src="../assets/logo.png" alt="Life Optimizer Logo" />
          </div>
        </router-link>
        <div class="register-form">
          <p>
            Already Have An Account?
            <router-link to="/login"> Log in!</router-link>
          </p>
          <form @submit.prevent="register">
            <div class="input-group">
              <label for="firstName">
                First name*
              </label>
              <input type="text" id="firstName" v-model="firstName" required />
            </div>
            <div class="input-group">
              <label for="lastName">
                Last name*
              </label>
              <input type="text" id="lastName" v-model="lastName" required />
            </div>
            <div class="input-group">
              <label for="email">
                Email address*
              </label>
              <input type="email" id="email" v-model="email" required />
            </div>
            <div class="input-group">
              <label for="password">
                Password*
              </label>
              <input
                :type="passwordVisible ? 'text' : 'password'"
                id="password"
                v-model="password"
                required
              />
              <font-awesome-icon
                :icon="passwordVisible ? 'eye' : 'eye-slash'"
                class="password-toggle"
                @click="togglePasswordVisibility"
              />
            </div>
            <div class="options">
              <label>
                <input type="checkbox" v-model="terms" required />
                I agree to <a href="#">Terms & Conditions</a> and acknowledge the <a href="#">Privacy Policy</a>.
              </label>
            </div>
            <button type="submit" class="register-button">Register</button>
          </form>
        </div>
      </div>
    </div>
  </template>
  <script>
  import axios from 'axios';
  
  export default {
    name: 'SignupPage',
    data() {
      return {
        firstName: '',
        lastName: '',
        email: '',
        password: '',
        terms: false,
        passwordVisible: false,
      };
    },
    methods: {
      async register() {
        try {
          const response = await axios.post('http://localhost:3000/register', {
            firstName: this.firstName,
            lastName: this.lastName,
            email: this.email,
            password: this.password,
          });
          console.log('Registration successful:', response.data);
        } catch (error) {
          console.error('Error registering:', error.response ? error.response.data : error.message);
        }
      },
      togglePasswordVisibility() {
        this.passwordVisible = !this.passwordVisible;
      },
    },
  };
  </script>
  
  <style scoped>
  #app {
    font-family: 'Times New Roman', Times, serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: hsl(210, 29%, 24%);
    background-color: white;
  }
  
  .navbar {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 10px 20px;
    background-color: #f8f9fa;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    position: relative;
  }
  
  .menu {
    display: flex;
    justify-content: flex-end;
    font-weight: bold;
  }
  
  .menu a {
    margin-left: 20px;
    text-decoration: none;
    color: #2c3e50;
  }
  
  .register-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  
  .register-logo img {
    width: 250px;
    margin-bottom: 30px;
  }
  
  .register-form {
    background: linear-gradient(135deg, #7864a2, #cfc5ff);
    padding: 50px;
    border-radius: 15px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
    color: white;
    width: 400px;
  }
  
  .register-form p {
    margin-bottom: 20px;
    font-size: 16px;
  }
  
  .input-group {
    position: relative;
    margin-bottom: 20px;
  }
  
  .input-group label {
    display: block;
    font-size: 16px;
    margin-bottom: 5px;
  }
  
  .input-group input {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    outline: none;
    background-color: #f0f0f0;
    font-size: 16px;
  }
  
  .password-toggle {
    position: absolute;
    top: 38px;
    right: 10px;
    cursor: pointer;
    color: #555;
  }
  
  .options {
    display: flex;
    align-items: center;
    font-size: 14px;
    margin-bottom: 20px;
  }
  
  .options label {
    margin-left: 5px;
  }
  
  .register-button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background-color: #e1e1e1;
    color: rgb(15, 14, 14);
    font-size: 16px;
    cursor: pointer;
  }
  
  .register-button:hover {
    background-color: #d1d1d1;
  }
  </style>
  