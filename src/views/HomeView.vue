<template>
  <div class="home">
    <AllArticles />
  </div>
</template>

<script>
// @ is an alias to /src
import AllArticles from "@/components/AllArticles.vue";

export default {
  name: "HomeView",
  components: {
    AllArticles,
  },
};
</script>
