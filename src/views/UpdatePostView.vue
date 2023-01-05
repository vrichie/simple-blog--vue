<template >
  <UpdateArticle v-bind:postId="id" />
</template>
<script>
import UpdateArticle from "@/components/UpdateArticle.vue";
export default {
  name: "UpdatePostView",
  components: {
    UpdateArticle,
  },
  data() {
    return {
      post: {},
      id: "",
    };
  },
  created() {
    this.id = this.$route.params.id;

    this.fetchPost(this.id);
  },
  methods: {
    async fetchPost(id) {
      try {
        const res = await fetch(`http://localhost:5000/posts/${id}`);
        const data = await res.json();
        // const rdata = await data;
        this.post = await data;
        // console.log(rdata);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
<style scoped>
h1,
p {
  text-align: left;
}
</style>