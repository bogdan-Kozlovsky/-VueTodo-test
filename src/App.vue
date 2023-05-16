<template>
  <div class="app">
    <Form @createPost="createNewPost"/>
    <Posts :posts="posts"/>
  </div>
</template>

<script>
import Posts from '@/components/Posts';
import Form from '@/components/Form';

export default {
  components: {
    Posts, Form
  },
  data() {
    return {
      posts: []
    }
  },
  methods: {
    createNewPost(post) {
      this.posts.push(post)
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

li {
  list-style: none;
}

.app {
  padding: 15px;
}
</style>
