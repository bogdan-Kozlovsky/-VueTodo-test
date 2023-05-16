<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
}
</script>

<style scoped>
.btn {
  background-color: transparent;
  padding: 5px 15px;
  display: block;
  border: 1px solid orange;
  cursor: pointer;
}
</style>
