<template>
  <div v-if="posts.length">
    <h3>List of Posts:</h3>
    <ul>
      <post
          v-for="post in posts"
          :post="post"
          :key="post.id"
          @remove="$emit('remove', post)"
      />
    </ul>
  </div>
  <h3 v-else>The list of posts is empty:</h3>
</template>

<script>
import Post from '@/components/Post'

export default {
  name: 'posts',
  components: {
    Post
  },
  props: {
    posts: {
      type: Array,
      required: true,
    }
  },
}
</script>

<style scoped>

</style>
