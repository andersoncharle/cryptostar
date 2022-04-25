<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <div class="user-profile__subpart">
        <h1 class="user-profile__username">@_{{ user.username }}</h1>
        <div class="user-profile__admin-badge" v-if="!user.isAdmin">Admin</div>
        <div class="user-profile__admin-badge" v-else>Not Admin</div>
        <div class="user-profile__follower-count" id="count">
          <strong>Followers:</strong>
          <span> {{ followers }}</span>
        </div>
        <div class="container">
          <form
            class="user-profile__create-tweet"
            @submit.prevent="createNewTweet"
            :class="{ '--exceeded': newTweetsCharacterCount > 180 }"
          >
            <label for="subject">
              <strong>new tweets:</strong>
              ({{ newTweetsCharacterCount }}/180)
            </label>
            <textarea
              id="subject"
              name="subject"
              placeholder="Write something.."
              style="height: 50px"
              v-model="newTweetContent"
            ></textarea>
            <div class="user-profile__create-tweets-type">
              <label for="newTweetsType">
                <strong>Type: </strong>
              </label>
              <select name="" id="newTweetsType" v-model="selectedTweetType">
                <option
                  :value="option.value"
                  v-for="(option, index) in tweetTypes"
                  :key="index"
                >
                  {{ option.name }}
                </option>
              </select>
            </div>
            <input type="submit" value="Tweeet it!" />
          </form>
        </div>
      </div>
    </div>
    <div class="user-profile__tweets-wrapper">
      <tweetItem
        v-for="items in user.tweetsLoop"
        :key="items.id"
        :username="user.username"
        :tweet="items"
        @favouriteMitnick="toggleFavourite"
      />
    </div>
  </div>
</template>

<script>
import tweetItem from "@/components/tweetItem";
export default {
  name: "userProfile",
  components: { tweetItem },
  data() {
    return {
      newTweetContent: "",
      selectedTweetType: "instant",
      tweetTypes: [
        { value: "draft", name: "Draft" },
        { value: "instant", name: "Instant Tweet" },
      ],
      followers: 0,
      user: {
        id: 1,
        username: "anderson",
        firstName: "mkakari",
        lastName: "chale",
        email: "andersondeveloper@gmail.com",
        isAdmin: false,
        tweetsLoop: [
          { id: 1, content: "blackmitnick is amazing buddy!!" },
          { id: 2, content: "code with blackmitnick for advanced concepts" },
          // { id: 3, content: "if it works never touch it again budahhh" },
          // { id: 4, content: "if it works never touch it again budahhh" },
          // { id: 5, content: "if it works never touch it again budahhh" },
        ],
      },
    };
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
    newTweetsCharacterCount() {
      return this.newTweetContent.length;
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
    toggleFavourite(id) {
      console.log(`favourites tweet is # ${id}`);
    },
    followUser: function () {
      this.followers++;
    },
    createNewTweet() {
      if (this.newTweetContent && this.selectedTweetType !== "draft") {
        this.user.tweetsLoop.unshift({
          id: this.user.tweetsLoop.length + 1,
          content: this.newTweetContent,
        });
        this.newTweetContent = "";
      }
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
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: 1fr;
  grid-column-gap: 1px;
  padding: 10px 5%;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 80px;
  margin-left: 150px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  /*padding: 60px;*/
  /*background-color: white;*/
  border-radius: 5px;
  border: 1px solid #dfe3eb;
  /*margin: 0 auto;*/
  background-color: MediumSeaGreen;
}
.user-profile__tweets-wrapper {
  display: inline-block;
  justify-content: start;
  /*align-items: center;*/
  width: 100%;
}

.user-profile__subpart {
  margin: 0 10px;
}

select,
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type="submit"] {
  background-color: #04aa6d;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: #45a049;
}

.container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  margin: 20px auto;
}
.--exceeded {
  color: red;
  border: 2px solid red;
}
.--exceeded input[type="submit"] {
  color: white;
  background-color: red;
}

.user-profile__admin-badge {
  background-color: rebeccapurple;
  color: wheat;
  display: block;
  border-radius: 6px;
  width: 70px;
  margin-bottom: 10px;
  padding: 2px 10px;
  text-transform: lowercase;
}

/*.user-profile__tweets-wrapper {*/
/*  !*display: flex;*!*/
/*  !*flex-direction: column;*!*/
/*  !*align-items: center;*!*/
/*  !*justify-content: center;*!*/
/*  !*margin-right: 50px;*!*/
/*  !*margin-top: 4px;*!*/
/*  !*box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);*!*/
/*  !*padding: 60px;*!*/
/*  !*background-color: white;*!*/
/*  !*border-radius: 5px;*!*/
/*  !*border: 1px solid #dfe3eb;*!*/
/*  !*margin: 0 auto;*!*/
/*  !*background-color: rebeccapurple;*!*/
/*}*/
</style>
