<template>
  <div class="app">
    <form @submit.prevent class="form">
      <label>
        title
        <input
            :value="titleValue"
            @input="titleValue = $event.target.value"
            type="text"
            class="input">
      </label>
      <label>
        description
        <input
            :value="descriptionValue"
            @input="descriptionValue = $event.target.value"
            type="text"
            class="input">
      </label>
    </form>

    <ul>
      <li class="post" v-for="post in posts">
        <p>
          <b>Name:</b>: {{ post.title }}
        </p>
        <p>
          <b>Description:</b>: {{ post.description }}
        </p>
      </li>
    </ul>

    <button
        @click="addNewPost"
        :disabled="!titleValue.length || !descriptionValue.length"
        class="btn">Add new post
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleValue: '',
      descriptionValue: '',
      posts: []
    }
  },
  methods: {
    addNewPost() {
      const newPost = {id: Date.now(), title: this.titleValue, description: this.descriptionValue}
      this.posts.push(newPost)
      this.titleValue = ''
      this.descriptionValue = ''
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

.post {
  border: 1px solid orange;
  padding: 15px;
  margin-bottom: 10px;
}

.form {
  margin-bottom: 15px;
}

.input {
  display: block;
  border: 1px solid orange;
  padding: 5px 15px;
  width: 100%;
  margin-bottom: 15px;
}

.btn {
  background-color: transparent;
  padding: 5px 15px;
  display: block;
  margin-left: auto;
  border: 1px solid orange;
}
</style>
