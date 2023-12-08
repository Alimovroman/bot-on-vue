<template>
  <div id="app">
    <MainPage />
  </div>
</template>

<script>
import MainPage from "./components/Main.vue";

export default {
  name: "App",
  components: {
    MainPage,
  },
};
</script>

<style>
#app {
  height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #7ca6cf;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
