  
<template>
    <div class="user-profile">
      <img :src="avatar" alt="User Avatar" class="avatar"/>
      <h2>{{ user.name }}</h2>
      <p><strong>Email:</strong> {{ user.email }}</p>
      <p><strong>Phone:</strong> {{ user.phone }}</p>
      <p><strong>Address:</strong> {{ fullAddress }}</p>
      <p><strong>Website:</strong> <a :href="user.website">{{ user.website }}</a></p>
      <p><strong>Company:</strong> {{ user.company.name }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      user: Object
    },
    computed: {
      avatar() {
        return `https://i.pravatar.cc/150?img=${this.user.id}`;
      },
      fullAddress() {
        const { street, suite, city, zipcode } = this.user.address;
        return `${street}, ${suite}, ${city}, ${zipcode}`;
      }
    }
  }
  </script>
  
  <style scoped>
  .user-profile {
    border: 1px solid #ddd;
    padding: 16px;
    margin: 16px;
    border-radius: 8px;
    max-width: 300px;
    text-align: center;
  }
  
  .avatar {
    border-radius: 50%;
    width: 150px;
    height: 150px;
    object-fit: cover;
  }
  </style>
  