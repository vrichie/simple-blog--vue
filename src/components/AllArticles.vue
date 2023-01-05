<template lang="">
    <div>
        <h1>
            All Articles
        </h1>
        <ul id="Cardwrapper" >

            <li v-for="article in articles" :key="article.id">

                <h2>
                    {{article.title}}
                </h2>
                <span>
                                 <p>
                    {{article.writer}}
                </p>  
                             <router-link :to="`/post/${article.id}`">
                Read
              </router-link>
              <router-link :to="`/update/${article.id}`">
                update
              </router-link>
              <button @click="deletePost(article.id)">delete</button>
                </span>

            </li>

        </ul>
    </div>
</template>
<script>
export default {
  name: "AllArticles",
  data() {
    return {
      articles: [],
    };
  },
  created() {
    this.fetchArticles();
  },
  methods: {
    async fetchArticles() {
      try {
        const res = await fetch("http://localhost:5000/posts");
        this.articles = await res.json();
        // console.log(res);
      } catch (e) {
        console.error(e);
      }
    },
    async deletePost(id) {
      console.log(id);
      try {
        const res = await fetch(`http://localhost:5000/posts/${id}`, {
          method: "DELETE",
        });
        // console.log(res);
        if (res.ok) {
          this.fetchArticles();
        }
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
<style  scoped>
div {
  margin: auto;
}
#Cardwrappper {
  width: 100%;
  margin: auto;
}
li {
  background: aliceblue;
  list-style: none;
  text-align: left;
  padding: 4px;
  margin-bottom: 10px;
  border-radius: 10px;
}
span {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>