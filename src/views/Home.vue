<template>
  <div class="home">
    <h1>All Posts</h1>
    <div v-for="post in posts">
      <!-- <p>User ID: {{ post.user_id }}</p> -->
      <p>Title: {{ post.title }}</p>
      <p>Body: {{ post.body }}</p>
      <p>Image: {{ post.image }}</p>
      <hr>
    </div>
  </div>
</template>

<script>

import axios from "axios";

export default {
  data: function() {
    return {
      posts: []
    };
  },
  created: function() {
    axios.get("/api/posts").then(response => {
      this.posts = response.data;
    });
  },
  methods: {}
};
</script>
