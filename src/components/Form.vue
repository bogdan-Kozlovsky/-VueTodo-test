<template>
  <form @submit.prevent class="form">
    <label>
      title
      <my-input v-model="post.titleValue"/>
    </label>
    <label>
      description
      <my-input v-model="post.descriptionValue"/>
    </label>

    <my-button @click="createPost"
               :disabled="!post.titleValue.length || !post.descriptionValue.length">
      Add new post
    </my-button>
  </form>

</template>

<script>

export default {
  data() {
    return {
      post: {
        titleValue: '',
        descriptionValue: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('createPost', this.post);
      this.post = {
        titleValue: '',
        descriptionValue: '',
      }
    }
  }
}
</script>

<style scoped>
.form {
  margin-bottom: 15px;
}

.form > button {
  margin-left: auto;
}
</style>
