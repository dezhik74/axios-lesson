<template>
  <div id="app">
    <h1>Тест AXIOSa</h1>
    <AlPost
      :posts="posts"
      :isError="isError"
    />
    <button v-if="!isLoaded" @click="buttClick">Загрузить</button>
  </div>
</template>

<script>

import AlPost from "./components/alPosts.vue";
import axios from "axios";
export default {
  name: 'App',
  components: {
    AlPost,
  },
  data() {
    return {
      posts: [],
      isError : false,
      isLoaded: false,
    }
  },
  methods: {
    buttClick() {
      this.loadPosts();
    },
    async loadPosts() {
      try {
        const res = await axios.get("https://jsonplaceholder.typicode.com/posts")
        this.isError = false;
        this.posts = res.data
      }
      catch (err) {
        this.isError = true
      }
      finally {
        this.isLoaded = true;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
