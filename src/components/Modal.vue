<template>
  <teleport to=".modals-container">
    <div class="modal">
      <h1>This is a modal</h1>
      <p>Lorem ipsijm dolor</p>
      <button>Hide modal</button>
    </div>
  </teleport>
</template>

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
