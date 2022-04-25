<template>
  <div id="app">
    <h1 class="glow-with_blackmitnick">code with anderson.</h1>

    <user-profile />
  </div>
</template>

<script>
import userProfile from "@/components/userProfile";
export default {
  name: "App",
  components: {
    userProfile,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body {
  background-image: linear-gradient(to right, #c93030, #8f2079);
}

#app {
  /*box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);*/
  /*padding: 50px;*/
  /*width: 50%;*/
  /*background-color: MediumSeaGreen;*/
  /*text-align: center;*/
  /*!*color: ghostwhite;*!*/
  /*margin: 0 auto 60px;*/
}

.glow-with_blackmitnick {
  font-size: 80px;
  color: #25a99e;
  text-align: center;
  text-transform: capitalize;
  animation: glow 1s ease-in-out infinite alternate;
}

@-webkit-keyframes glow {
  from {
    text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #e60073,
      0 0 40px #e60073, 0 0 50px #e60073, 0 0 60px #e60073, 0 0 70px #e60073;
  }

  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #ff4da6, 0 0 40px #ff4da6,
      0 0 50px #ff4da6, 0 0 60px #ff4da6, 0 0 70px #ff4da6, 0 0 80px #ff4da6;
  }
}
</style>
