<template>
  <div class="app">
    <my-button @click="showModal">create a post</my-button>

    <my-modal v-model:show="isShowModal">
      <form @createPost="createNewPost"/>
    </my-modal>

    <posts :posts="posts" @remove="removePost" v-if="!isLoading"/>

    <h1 v-else>Loading</h1>
  </div>
</template>

<script>
import Posts from '@/components/Posts';
import Form from '@/components/Form';
import MyModal from "@/components/UI/MyModal";
import axios from 'axios';

export default {
  components: {
    MyModal,
    Posts, Form
  },
  data() {
    return {
      posts: [],
      isShowModal: false,
      isLoading: false,
    }
  },
  methods: {
    createNewPost(post) {
      this.posts.push(post)
      this.isShowModal = false
    },
    removePost(post) {
      this.posts = this.posts.filter(el => el.id !== post.id)
    },
    showModal() {
      this.isShowModal = true
    },
    async fetchPosts() {
      try {
        this.isLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
      } catch (e) {
        console.log(e)
      } finally {
        this.isLoading = false
      }
    }
  },
  mounted() {
    this.fetchPosts()
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
