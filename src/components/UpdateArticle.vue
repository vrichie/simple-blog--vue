<template lang="">
  <form @submit="handleSubmit">
    <h1>
        Update The Post
    </h1>
    <span>
      <label for="title"> the title</label>
      <input type="text" name="title" v-model="title" required />
    </span>
    <br />
    <span>
      <label for="body"> the body</label>
      <textarea name="body" id="body" rows="10" v-model="body" required></textarea>
    </span>
    <br />
    <span>
      <label for="writer"> written by</label>
      <input type="text" name="writer" v-model="writer" required />
    </span>

    <button type="submit">{{text}}</button>
  </form>
</template>
<script>
export default {
  name: "CreateArticle",
  props: {
    postId: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      title: "",
      body: "",
      writer: "",
      text: "update Post",
    };
  },
  created() {
    this.getData();
  },
  methods: {
    async getData() {
      // console.log(id);
      try {
        const res = await fetch(`http://localhost:5000/posts/${this.postId}`);
        const data = await res.json();
        const rdata = await data;
        console.log(data);
        this.title = rdata.title;
        this.body = rdata.body;
        this.writer = rdata.writer;
      } catch (error) {
        console.error(error);
      }
    },
    async handleSubmit(e) {
      e.preventDefault();
      const data = {
        title: this.title,
        body: this.body,
        writer: this.writer,
      };
      try {
        const res = await fetch(`http://localhost:5000/posts/${this.postId}`, {
          method: "PUT",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(data),
        });
        if (res.ok) {
          console.log("Post updated successfully");

          this.text = "Post updated";
        } else {
          //   console.log("Error submitting post");
          this.text = "failed to create";
        }
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
<style scoped>
form {
  width: 100%;
  padding: 20px;
  margin-bottom: 20px;
  background-color: aliceblue;
  border-radius: 10px;
}
span {
  margin: 5px;
  display: flex;
  align-items: flex-start;
  justify-content: baseline;
  flex-direction: column;
}
label {
  font-size: 14px;
  margin-bottom: 5px;
}
input,
textarea {
  outline: none;
  border: none;
  background-color: transparent;
  border-bottom: 1px solid grey;
  padding: 2px;
  width: 100%;
  font-size: 16px;
}
button {
  margin-top: 10px;
  border: 1px solid slateblue;
  border-radius: 10px;
  background-color: transparent;
  outline: none;
  padding: 5px 20px;
}
</style>
