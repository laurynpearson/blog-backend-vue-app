<template>
  <div class="new posts">
    <h1>{{ message }}</h1>
    <p>Title: <input type="text" v-model="newPostTitle"></p>
    <p>Body: <input type="text" v-model="newPostBody"></p>
    <p>Image: <input type="text" v-model="newPostImage"></p>
    <button v-on:click="createPost()">Create Post</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to the New Posts Page!!",
      newPostTitle: "",
      newPostBody: "",
      newPostImage: ""
    };
  },
  created: function() {},
  methods: {
    createPost: function() {
      var newPost = {
        title: this.newPostTitle,
        body: this.newPostBody,
        image: this.newPostImage
      };
      axios.post("/api/posts", newPost).then(response => {
        console.log('in the callback for create');
        console.log(response.data);
        this.$router.push('/');
      });
    }
  }
};
</script>