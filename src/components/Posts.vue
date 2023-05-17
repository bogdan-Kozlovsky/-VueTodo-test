<template>
  <div v-if="posts.length">
    <h3>List of Posts:</h3>
    <ul>
      <transition-group name="list">
        <post
            v-for="post in posts"
            :post="post"
            :key="post.id"
            @remove="$emit('remove', post)"
        />
      </transition-group>
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
.list-item {
  display: inline-block;
  margin-right: 10px;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.4s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.list-move {
  transition: transform 0.4s ease;
}
</style>
