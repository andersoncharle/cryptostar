<template>
  <div id="app">
    <user-profile/>

  </div>
</template>

<script>
import userProfile from "@/components/userProfile";
export default {
  name: "App",
  components:{
    userProfile
  }
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

</style>
