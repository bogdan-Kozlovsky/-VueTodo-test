<template>
  <ul>
    <Post v-for="post in posts" :post="post"/>
  </ul>
</template>

<script>
import Post from '@/components/Post'

export default {
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
