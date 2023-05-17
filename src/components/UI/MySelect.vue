<template>
  <select :value="modelValue" @input="changeOption($event.target.value)">
    <option disabled value="">Choose from the list</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'my-select',
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => [],
      require: true,
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event)
    }
  }
}
</script>

<style scoped>

</style>
