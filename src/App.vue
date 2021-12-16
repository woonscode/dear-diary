<template>
  <div class="bg-light border border-primary">
    <img alt="Vue logo" src="./assets/logo.png">
    <Post :msg="Sameple"></Post>
  </div>
</template>

<script>
import Post from './components/Post.vue'

export default {
  data() {
    return {
      Sameple: "E"
    }
  },

  name: 'App',
  components: {
    Post
  },

  methods: {
    submit() {
      
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
