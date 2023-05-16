<template>
  <li class="post">
    <div>
      <p>
        <b>Name:</b>: {{ post.titleValue }}
      </p>
      <p>
        <b>Description:</b>: {{ post.descriptionValue }}
      </p>
    </div>

    <my-button>Delete</my-button>
  </li>
</template>

<script>
import MyButton from '@/components/UI/MyButton';

export default {
  components: {MyButton},

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
