<template>
  <input
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      class="input"
  />
</template>

<script>
export default {
  name: 'my-input',
  props: {
    modelValue: String,
  },
  emits: ['update:modelValue'],
}
</script>

<style scoped>
.input {
  display: block;
  border: 1px solid orange;
  padding: 5px 15px;
  width: 100%;
  margin-bottom: 15px;
}
</style>
