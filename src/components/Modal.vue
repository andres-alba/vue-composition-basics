<template>
  <teleport to=".modals-container">
    <div class="modal">
      <h1>{{ title }}</h1>
      <p>Lorem ipsijm dolor</p>
      <slot></slot>
      <button @click="handleButtonClick">Hide modal</button>
    </div>
  </teleport>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    default: 'No title specified',
  },
})

const emit = defineEmits(['hideModal'])

const handleButtonClick = () => {
  emit('hideModal')
}
</script>

<style>
.modal {
  background: red;
  padding: 10px;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
</style>
