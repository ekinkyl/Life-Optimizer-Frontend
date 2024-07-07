<template>
    <div>
      <router-view></router-view>
    </div>
    <div id="app">
      <nav class="navbar">
        <div class="hamburger" @click="toggleSidebar">
          &#9776;
        </div>
        <div class="menu">
          <a href="#">Help</a>
          <router-link to="/login">Log In</router-link>
        </div>
      </nav>
      <aside class="sidebar" :class="{ open: isSidebarOpen }">
        <ul>
          <li><a href="#">Nutrition Diary</a></li>
          <li><a href="#">Motion Diary</a></li>
          <li><a href="#">Sleep Insights</a></li>
          <li><a href="#">Suggestions</a></li>
          <li><a href="#">Wellness Club</a></li>
          <li><a href="#">Reminders</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Data Sharing</a></li>
        </ul>
      </aside>
      <main @click="closeSidebar">
        <div class="content-container">
          <div class="text-container">
            <div class="logo-container">
              <a href="/">
                <img class="logo" alt="Vue logo" src="../assets/logo.png">
              </a>
            </div>
            <header class="main-header">
              <h1 class="header-title">Optimize Your Health</h1>
              <p class="header-description">Maximize your health and life with personalized insights and recommendations powered. Our app creates a "digital twin" of your daily habits and health data, providing tailored suggestions to enhance your wellbeing.</p>
            </header>
            <div class="sub-container">
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Nutrition Diary</h2>
                  <p class="sub-header-description">Record what you eat and take control of your eating habits.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage2.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Motion Diary</h2>
                  <p class="sub-header-description">Record your workouts and improve your performance.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage7.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Sleep Insights</h2>
                  <p class="sub-header-description">Track your sleep time and create regular sleep habits.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage8.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Suggestions</h2>
                  <p class="sub-header-description">Connect with friends and share your activities. Motivate each other.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage3.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Wellness Club</h2>
                  <p class="sub-header-description">Record what you eat and take control of your eating habits.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage9.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Reminders</h2>
                  <p class="sub-header-description">Get notifications reminding you to take your medications, drink water, and do other important activities on time.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage4.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Blog</h2>
                  <p class="sub-header-description">Read blog posts about topics that interest you. Learn more about the lifestyle that appeals to you.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage5.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
              <div class="sub-section">
                <div class="sub-text">
                  <h2 class="sub-header">Data Sharing</h2>
                  <p class="sub-header-description">Share your health data and progress with anyone you want.</p>
                </div>
                <div class="sub-image">
                  <img src="../assets/homepage6.jpg" alt="Health Image" class="side-image">
                </div>
              </div>
            </div>
          </div>
          <div class="image-container">
            <img src="../assets/homepage.jpg" alt="Health Image" class="side-image">
          </div>
        </div>
      </main>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PageHome',
    data() {
      return {
        isSidebarOpen: false,
        handleClickOutside: this.closeSidebar
      };
    },
    methods: {
      toggleSidebar() {
        this.isSidebarOpen = !this.isSidebarOpen;
      },
      closeSidebar() {
        if (this.isSidebarOpen) {
          this.isSidebarOpen = false;
        }
      }
    },
    mounted() {
      // Close sidebar when clicking outside of it
      document.addEventListener('click', this.handleClickOutside);
    },
    unmounted() {
      // Clean up event listener when component is destroyed
      document.removeEventListener('click', this.handleClickOutside);
    }
  }
  </script>
  
  <style>
  #app {
    font-family: 'Times New Roman', Times, serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: hsl(210, 29%, 24%);
  }
  
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    background-color: #f8f9fa;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    position: relative;
  }
  
  .content-container {
    display: flex;
    align-items: flex-start;
  }
  
  .image-container {
    flex: 1;
    text-align: center;
    margin-top: 100px; /* Adjust the margin to move the image down */
  }
  
  .side-image {
    width: 100%;
    max-width: 1500px; /* Increase max-width to make the image larger */
    margin: 0 auto; /* Center the image horizontally */
    display: block; /* Ensures the image takes full width */
    margin-left: 20px;
  }
  
  .text-container {
    flex: 2;
    text-align: left;
  }
  
  .logo-container {
    margin: 20px 20px 20px 0; /* Adjust the margin as needed */
    margin-left: 50px;
  }
  
  .logo {
    width: 250px;
  }
  
  .main-header {
    margin-left: 20px; /* Adjust the margin as needed */
    transition: margin-left 0.3s ease;
  
  }
  
  .header-title {
    color: #7864a2;
    font-size: 60px;
    margin-left: 150px; /* Adjust the margin as needed */
  }
  
  .header-description {
    font-size: 25px;
    width: 80%;
    margin: 10px 0;
    margin-left: 50px; /* Adjust the margin as needed */
  }
  
  .sub-container {
    display: flex;
    flex-direction: column;
  }
  
  .sub-section {
    display: flex;
    align-items: center;
    margin: 20px 0;
  }
  
  .sub-text {
    flex: 2;
  }
  
  .sub-header {
    margin-left: 70px;
    color: #7864a2;
    font-size: 50px;
  }
  
  .sub-header-description {
    font-size: 25px;
    width: 80%;
    margin: 10px 0;
    margin-left: 70px; /* Adjust the margin as needed */
  }
  
  .sub-image {
    flex: 1;
    text-align: center;
  }
  
  .sub-image img {
    max-width: 400px; /* Set the desired width for the image */
    margin-left: 400px;
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
  
  .hamburger {
    display: flex;
    align-items: center;
    cursor: pointer;
    font-size: 24px;
  }
  
  .sidebar {
    position: fixed;
    top: 0;
    left: -220px;
    width: 200px;
    height: 100%;
    background-color: #f8f9fa;
    color: hsl(210, 29%, 24%);
    padding-top: 60px;
    transition: left 0.3s ease;
  }
  
  .sidebar.open {
    left: 0;
  }
  
  .sidebar ul {
    list-style-type: none;
    padding: 0;
  }
  
  .sidebar ul li {
    padding: 10px 20px; /* Adjust this padding to move the text to the right */
    text-align: left;
    font-weight: bold;
    margin-bottom: 40px; /* Adds space between the list items */
  
  }
  
  .sidebar ul li a {
    text-decoration: none;
    color: hsl(210, 29%, 24%);
    display: block;
  }
  
  main {
    padding: 20px;
    transition: margin-left 0.3s ease;
  }
  
  .sidebar.open + main {
    margin-left: 220px;
  }
  
  
  
  </style>
  