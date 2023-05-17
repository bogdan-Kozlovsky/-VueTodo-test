<template>
  <div class="modal" v-if="show" @click.stop="isShowModal">
    <div @click.stop class="modal-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-modal',
  props: {
    show: {
      type: Boolean,
      default: false,
      require: true,
    }
  },
  methods: {
    isShowModal() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.modal-content {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  max-width: 400px;
  width: 100%;
  text-align: center;
}
</style>
