<template>
  <div class="app-layout">
    <slot name="header"></slot>
    <slot name="scheduler"></slot>
    <slot name="list"></slot>
    <slot name="floating-button"></slot>
    <Modal v-if="isModalVisible" />
  </div>
</template>

<script>
import { inject } from "vue";
import Modal from "./Modal.vue";

export default {
  setup() {
    const isModalVisible = inject("isModalVisible");
    return { isModalVisible };
  },
  components: { Modal },
};
</script>

<style>
.app-layout {
  background-color: var(--white);
  width: 390px;
  height: 800px;

  /* max-width: 480px; */
  margin: 40px auto;

  padding: 24px;

  border-radius: var(--border-radius-lg);

  -webkit-box-shadow: 10px 10px 42px 8px rgba(135, 127, 175, 0.25);
  -moz-box-shadow: 10px 10px 42px 8px rgba(135, 127, 175, 0.25);
  box-shadow: 10px 10px 42px 8px rgba(135, 127, 175, 0.25);

  position: relative;
}
</style>
