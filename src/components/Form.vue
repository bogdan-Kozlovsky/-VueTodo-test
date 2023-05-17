<template>
  <form @submit.prevent class="form">
    <label>
      title
      <my-input v-model="post.title"/>
    </label>
    <label>
      description
      <my-input v-model="post.body"/>
    </label>

    <my-button @click="createPost"
               :disabled="!post.title.length || !post.body.length">
      Add new post
    </my-button>
  </form>

</template>

<script>

export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('createPost', this.post);
      this.post = {
        title: '',
        body: '',
      }
    }
  }
}
</script>

<style scoped>
.form > button {
  margin-left: auto;
}
</style>
