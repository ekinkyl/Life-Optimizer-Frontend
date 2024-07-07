<template>
    <div id="app">
      <nav class="navbar">
        <div class="menu">
          <a href="#">Help</a>
          <router-link to="/login">Log In</router-link>
        </div>
      </nav>
      <div class="login-container">
        <router-link to="/" class="logo-link"> <!-- Burada router-link ekledik -->
        <div class="login-logo">
          <img src="../assets/logo.png" alt="Life Optimizer Logo" />
        </div>
      </router-link>
        <div class="login-form">
          <h2>Welcome to Life Optimizer!</h2>
          <form @submit.prevent="login">
            <div class="input-group">
              <label for="email">
                <font-awesome-icon icon="envelope" />
                Email
              </label>
              <input type="email" id="email" v-model="email" required />
            </div>
            <div class="input-group">
              <label for="password">
                <font-awesome-icon icon="lock" />
                Password
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
                <input type="checkbox" v-model="rememberMe" />
                Remember me
              </label>
              <a href="#">Forgot password</a>
            </div>
            <button type="submit" class="login-button">Log In</button>
          </form>
          <p>
            Don't you have an account yet?
            <router-link to="/signup"> Sign up</router-link>
          </p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'LoginPage',
    data() {
      return {
        email: '',
        password: '',
        rememberMe: false,
        passwordVisible: false,
      };
    },
    methods: {
      login() {
        console.log('Email:', this.email);
        console.log('Password:', this.password);
        console.log('Remember me:', this.rememberMe);
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
  
  .login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  
  .login-logo img {
    width: 250px;
    margin-bottom: 30px;
  }
  
  .login-form { 
    background: linear-gradient(135deg, #7864a2, #cfc5ff);
    padding: 50px;
    border-radius: 15px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
    color: white;
    width: 400px;
}

  
  .login-form h2 {
    margin-bottom: 20px;
    font-size: 24px;
    font-weight: bold;
  }
  
  .input-group {
    position: relative;
    margin-bottom: 20px;
  }
  
  .input-group label {
    display: flex;
    align-items: center;
    font-size: 16px;
    margin-bottom: 5px;
  }
  
  .input-group label font-awesome-icon {
    margin-right: 10px;
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
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
    margin-bottom: 20px;
  }
  
  .login-button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background-color: #e1e1e1;
    color: rgb(15, 14, 14);
    font-size: 16px;
    cursor: pointer;
  }
  
  .login-button:hover {
    background-color: #e1e1e1;
  }
  
  .login-form p {
    margin-top: 20px;
  }
  
  .login-form p a {
    color: #ecf0f1;
    text-decoration: none;
  }
  
  .login-form p a:hover {
    text-decoration: underline;
  }
  </style>
  