<template>
  <div id="app">
    <h1>user id:{{ user.id }}</h1>
    <br />
    <div class="">
      <p>{{ user.firstName }} {{ user.lastName }}</p>
      <p>@_{{ fullName }}</p>

      <p><strong>Followers:</strong>{{ followers }}</p>
      <button @click="followUser" class="button button2">Followers</button>
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
  watch:{
    followers(newFollowerCount,oldFollowerCount){
      console.log(`${this.user.username} has gained new`);
    }
  },
  methods: {
    followUser: function () {
      this.followers++;
    },
  },
  mounted() {
    /*
     * life cycle hook
     * */

    this.followUser();
  },
};
</script>

<style>
body {
  background-image: linear-gradient(to right, #c93030, #8f2079);
}
#app {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  padding: 50px;
  width: 50%;
  background-color: MediumSeaGreen;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: ghostwhite;
  margin: 0 auto 60px;
}
.button {
  border-radius: 12px;
  background-color: #b3efb6; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
}

.button2:hover {
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.24),
    0 17px 50px 0 rgba(0, 0, 0, 0.19);
}
</style>
