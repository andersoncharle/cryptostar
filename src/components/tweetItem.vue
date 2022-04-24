<template>
  <div class="twoot-item" @click="favouriteTweets(tweet.id)">
    <div class="twoot-item__user">@{{ username }}</div>
    <div class="twoot-item__content">
      {{ tweet.content }}
    </div>
  </div>
</template>

<script>
export default {
  name: "tweetItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    tweet: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favouriteTweets(id) {
      this.$emit("favouriteMitnick", id);
    },
  },
};
</script>

<style scoped>
.twoot-item {
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #dfe3eb;
  box-sizing: border-box;
  cursor: pointer;
  margin: 10px auto;
  transition: all 0.25s ease;
}
.twoot-item:hover {
  transform: scale(1.1, 1.1);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.twoot-item__user {
  font-weight: bold;
}
</style>
