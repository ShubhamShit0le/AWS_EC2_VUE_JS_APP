<!-- src/App.vue -->
<template>
  <div id="app">
    <header>User Management</header>
    <main>
      <AddUser @user-added="fetchUsers" />
      <UserList ref="userList" />
    </main>
  </div>
</template>

<script>
import AddUser from './components/AddUser.vue';
import UserList from './components/UserList.vue';

export default {
  name: 'App',
  components: {
    AddUser,
    UserList
  },
  methods: {
    fetchUsers() {
      this.$refs.userList.fetchUsers();
    }
  }
};
</script>
