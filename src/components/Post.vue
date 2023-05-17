<template>
  <li class="post">
    <div>
      <p>
        <b>Name:</b>: {{ post.title }}
      </p>
      <p>
        <b>Description:</b>: {{ post.body }}
      </p>
    </div>

    <my-button @click="$emit('remove', post)">Delete</my-button>
  </li>
</template>

<script>

export default {
  name: 'post',
  props: {
    post: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>
.post {
  border: 1px solid orange;
  padding: 15px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
