<template>
  <!--  <h1>user id:{{ user.id }}</h1>-->
  <!--  <br />-->
  <!--  <div class="">-->
  <!--    <p>{{ user.firstName }} {{ user.lastName }}</p>-->
  <!--    <p>@_{{ fullName }}</p>-->

  <!--    <p><strong>Followers:</strong>{{ followers }}</p>-->
  <!--    <button @click="followUser" class="button button2">Followers</button>-->
  <!--  </div>-->
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <div class="user-profile__admin-badge">
        Admin
      </div>
      <h1 class="user-profile__username">@_{{ user.username }}</h1>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong>
        <p>{{ followers }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "userProfile",
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
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained new followers`);
      }
    },
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

<style scoped>
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
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  /*width: 100%;*/
  /*padding: 50px 5%;*/
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  /*margin-right: 50px;*/
  padding: 60px;
  /*background-color: white;*/
  border-radius: 5px;
  border: 1px solid #dfe3eb;
  text-align: center;
  margin: 0 auto;
}
.user-profile__admin-badge{
  background-color: rebeccapurple;
  color: wheat;
  border-radius: 6px;
margin-right: auto;
  padding: 0 10px;
}
</style>
