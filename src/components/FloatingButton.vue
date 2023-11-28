<template>
  <div class="floating-container">
    <button
      class="floating-button"
      :class="isModalVisible && 'active'"
      @click="onVisibleModalHandler"
    >
      +
    </button>
  </div>
</template>

<script>
import { inject } from "vue";

export default {
  setup() {
    const isModalVisible = inject("isModalVisible");
    const showModal = inject("showModal");
    const closeModal = inject("closeModal");

    const onVisibleModalHandler = () => {
      if (isModalVisible.value) {
        closeModal();
      } else {
        showModal();
      }
    };

    return { isModalVisible, onVisibleModalHandler };
  },
};
</script>

<style>
.floating-container {
  position: absolute;
  bottom: 24px;
  right: 24px;
  z-index: 9;
}

.floating-button {
  width: 60px;
  height: 60px;
  border-radius: var(--border-radius-full);
  background-color: var(--purple-dark);
  color: var(--white);
  font-size: 32px;
  transition: all 0.2s ease-in-out;
}

.floating-button:hover {
  background-color: var(--purple);
}

.active {
  transform: rotate(45deg);
}
</style>
