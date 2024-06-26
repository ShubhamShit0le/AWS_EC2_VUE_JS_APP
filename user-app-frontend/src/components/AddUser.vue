<!-- src/components/AddUser.vue -->
<template>
    <div>
      <h2>Add User</h2>
      <form @submit.prevent="addUser">
        <div>
          <label for="name">Name:</label>
          <input type="text" v-model="name" required />
        </div>
        <div>
          <label for="email">Email:</label>
          <input type="email" v-model="email" required />
        </div>
        <button type="submit">Add User</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        name: '',
        email: ''
      };
    },
    methods: {
      addUser() {
        axios.post('http://localhost:3000/users', {
          name: this.name,
          email: this.email
        })
        .then(() => {
          alert('User added successfully');
          this.name = '';
          this.email = '';
          this.$emit('user-added');
        })
        .catch(error => {
          console.error('There was an error!', error);
        });
      }
    }
  };
  </script>
  