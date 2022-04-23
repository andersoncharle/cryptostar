<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">@_{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="!user.isAdmin">Admin</div>
      <div class="user-profile__admin-badge" v-else>Not Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong>
        <span> {{ followers }}</span>
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
        isAdmin: false,
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
  width: 100%;
  padding: 50px 5%;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  /*padding: 60px;*/
  /*background-color: white;*/
  border-radius: 5px;
  border: 1px solid #dfe3eb;
  /*margin: 0 auto;*/
  background-color: MediumSeaGreen;
}
.user-profile__admin-badge {
  background-color: rebeccapurple;
  color: wheat;
  border-radius: 6px;
  margin-right: auto;
  margin-bottom: 10px;
  padding: 2px 10px;
  text-transform: lowercase;
}
</style>
