<template >
  <div>
    <h1>{{ post.title }}</h1>
    <p>By:{{ post.writer }}</p>
    <p>{{ post.body }}</p>
  </div>
</template>
<script>
export default {
  name: "PostView",
  data() {
    return {
      post: {},
    };
  },
  created() {
    const id = this.$route.params.id;
    console.log(id);
    this.fetchPost(id);
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