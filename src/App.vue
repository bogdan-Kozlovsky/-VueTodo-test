<template>
  <div class="app">
    <my-modal v-model:show="isShowModal">
      <Form @createPost="createNewPost"/>
    </my-modal>

    <div style="display: flex; justify-content: space-between">
      <my-button @click="showModal">create a post</my-button>

      <my-select
          v-model="selectedSort"
          :options="selectedOptions"
      />

    </div>

    <posts :posts="posts" @remove="removePost" v-if="!isLoading"/>

    <h1 v-else>Loading</h1>
  </div>
</template>

<script>
import Posts from '@/components/Posts';
import Form from '@/components/Form';
import MyModal from "@/components/UI/MyModal";
import axios from 'axios';
import MySelect from "@/components/UI/MySelect";

export default {
  components: {
    MySelect,
    MyModal,
    Posts, Form
  },
  data() {
    return {
      posts: [],
      isShowModal: false,
      isLoading: false,
      selectedSort: '',
      selectedOptions: [
        {value: 'title', name: 'Name'},
        {value: 'body', name: 'Body'},
      ],
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
    },
  },
  mounted() {
    this.fetchPosts()
  },
  watch: {
    selectedSort(newSelected) {
      this.posts.sort((a, b) => a[newSelected].localeCompare(b[newSelected]))
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
