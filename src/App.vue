<template>
  <div id="app">
    <h1>{{ user.id }}</h1>
    <br />
    <div>
      <p>{{ user.firstName }} {{ user.lastName }}</p>
      {{ fullName }} <br />

      {{ user }}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "anderson",
        firstName: "mkakari",
        lastName: "chale",
        email: "andersondeveloper@gmail.com",
        isAdmin: true,
      },
    };
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
