<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" :start="5" /> -->
  <Indecision />
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    Indecision,
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
