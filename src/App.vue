<template>
  <div id="main" class="container border border-warning border-4 rounded-3 p-2">
    <div id="top" class="border border-light border-3 rounded-pill bg-warning">
      <div class="text-center h2 fw-bold pt-1">Dear Diary</div>
    </div>
    <div class="accordion mt-2" id="main-body">
      <div class="accordion-item">
        <h2 class="accordion-header" id="new-post-header">
          <button class="fw-bold accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#new-post" aria-expanded="true" aria-controls="new-post">
            New Post
          </button>
        </h2>
        <div id="new-post" class="accordion-collapse collapse show" aria-labelledby="new-post-header">
          <div class="accordion-body">
            <div class="container bg-success p-2 border border-5 rounded-3">
              <input type="text" class="form-control" v-model="new_subject" placeholder="Subject">
              <textarea @keyup.enter="publish" class="form-control my-2" v-model="new_message" placeholder="Write your message here!"></textarea>
              <div class="d-grid">
                <button @click="publish" class="btn btn-info fw-bold">Publish</button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="accordion-item">
        <h2 class="accordion-header" id="all-posts-header">
          <button class="fw-bold accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#all-posts" aria-expanded="false" aria-controls="all-posts">
            All Posts
          </button>
        </h2>
        <div id="all-posts" class="accordion-collapse collapse" aria-labelledby="all-posts-header">
          <div class="accordion-body">
            <Post v-for="(post, index) in all_posts" :key="index" :message="post.message" :subject="post.subject" :date="post.date"></Post>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Post from './components/Post.vue'

export default {
  data() {
    return {
      new_subject: "",
      new_message: "",
      all_posts: []
    }
  },

  name: 'App',
  components: {
    Post
  },

  methods: {
    publish() {
      if (this.new_subject != "" && this.new_message != "") {
        // Get current date and format it into a more readable state
        let current_date = Date()
        let index_to_cut = current_date.indexOf("GMT")
        let formatted_date = current_date.substring(0, index_to_cut-1)

        // Construct object from input details
        let new_post = {
          subject: this.new_subject,
          message: this.new_message,
          date: formatted_date
        }
        this.all_posts.unshift(new_post)
        
        // Reset new post data
        this.new_subject = ""
        this.new_message = ""
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
  color: #2c3e50;
  margin-top: 60px;

}
#main {
  background-color: lightblue;
}
.accordion-button.collapsed {
  background-color: rgb(193, 255, 198);
}
</style>
