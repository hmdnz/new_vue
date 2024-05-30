<!-- src/App.vue -->
<template>
  <div id="app">
    <h1>User Profiles</h1>
    <div class="profiles-container">
      <UserProfile v-for="user in users" :key="user.id" :user="user" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import UserProfile from './components/UserProfile.vue';

export default {
  name: 'App',
  components: {
    UserProfile
  },
  data() {
    return {
      users: []
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users');
        this.users = response.data;
      } catch (error) {
        console.error('Error fetching users:', error);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.profiles-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
