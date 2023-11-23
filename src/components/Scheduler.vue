<template>
  <div class="scheduler">
    <Calendar expanded borderless :attributes="attributes" />
  </div>
</template>

<script setup>
import { Calendar } from "v-calendar";
import "v-calendar/style.css";
import { ref } from "vue";

const attributes = ref([
  {
    key: "today",
    highlight: true,
    dates: new Date(),
  },
]);
</script>

<style scoped>
.scheduler {
  width: 100%;
  padding: 8px;
}

.scheduler :deep(.vc-title) {
  font-family: "KCC-Ganpan";
  color: var(--purple);
  background-color: transparent;
}
.scheduler :deep(.vc-arrow) {
  color: var(--purple);
  background-color: transparent;
}
.scheduler :deep(.vc-weekday) {
  font-family: "KCC-Ganpan";
  font-weight: 400;
  color: var(--purple);
}
.scheduler :deep(.vc-day) {
  font-family: "KCC-Ganpan";
  font-weight: 400;
  color: var(--purple);
}

.scheduler :deep(.vc-highlight-bg-solid) {
  background-color: var(--purple);
}
</style>
