<template>
  <div class="welcome-container">
    <div class="header">
      <img src="/images/login.jpg" alt="Scenic View" class="header-image">
      <div class="user-controls">
        <router-link :to="{name: 'invoices'}" class="account-link">
          <button class="account-button">Account</button>
        </router-link>
        <button @click="logout" class="logout-button">Log Out</button>
        <div class="goback">
          <GoBack />
        </div>

      </div>
    </div>
    <div class="welcome-message">
      <h1>Welcome, {{ username }}</h1>
    </div>
  </div>
</template>

<script>
import GoBack from "@/components/GoBack.vue";

export default {
  components: {GoBack},
  data() {
    return {
      username: window.user
    }
  },
  methods: {
    logout() {
      window.user = null
      this.$router.push({name: 'Home', query: {logout: 'true'}})
    }
  }
}
</script>

<style scoped>
.welcome-container {
  font-family: 'Arial', sans-serif;
  background: #f3f4f6;
  text-align: center;
}
.header {
  position: relative;
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.header-image {
  width: 60%;
  height: auto;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.user-controls {
  position: absolute;
  top: 20px;
  right: 20px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

button {
  padding: 10px 20px;
  margin-bottom: 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 16px;
  font-weight: bold;
}
.account-button {
  background-color: #5cb85c; /* Green */
  color: #fff;
}
.logout-button {
  background-color: #d9534f; /* Red */
  color: #fff;
}

button:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

.welcome-message {
  padding: 20px 0;
}

h1 {
  font-size: 2.5rem;
  color: #333;
  margin-top: 0;
  margin-bottom: 8px;
}

@media (max-width: 768px) {
  .user-controls {
    right: 10px;
  }
}
</style>
