<template>
  <NavBarVue name="Blog" />
  <router-view />
</template>


<script>
import NavBarVue from "./components/NavBar.vue";
export default {
  name: "App",
  components: {
    NavBarVue,
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
}
body {
  padding: 0;
  margin: 0;
}
</style>
