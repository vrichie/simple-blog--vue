<template>
  <NavBarVue name="Blog" />
  <router-view />
  <BlogFooter />
</template>


<script>
import NavBarVue from "./components/NavBar.vue";
import BlogFooter from "./components/BlogFooter.vue";
export default {
  name: "App",
  components: {
    NavBarVue,
    BlogFooter,
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
