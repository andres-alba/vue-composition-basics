<template>
  <div class="modals">
    <h1>Modals</h1>
    <Modal v-if="showModal" title="My modal title (via prop)"> <p>Lorem psum dolor sit amet</p></Modal>
    <button @click="showModal = true">Show modal</button>
  </div>
</template>
<script setup>
// imports
import { ref } from 'vue'
import Modal from '@/components/Modal.vue'

//modals
const showModal = ref(false)
</script>
