<template>
  <div class="scheduler">
    <Calendar
      expanded
      borderless
      :attributes="attributes"
      @dayclick="onDayClickHandler"
    />
  </div>
</template>

<script setup>
import { Calendar } from "v-calendar";
import "v-calendar/style.css";
import { ref, inject } from "vue";

const selectedDate = inject("selectedDate");
const onDayClickHandler = inject("onDayClickHandler");
const attributes = ref([
  {
    key: "today",
    highlight: true,
    dates: new Date(),
  },
  {
    highlight: {
      fillMode: "outline",
    },
    dates: selectedDate,
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

.scheduler :deep(.vc-highlight-bg-outline) {
  border-color: var(--purple);
}

.scheduler :deep(.vc-highlight-content-outline) {
  font-family: "KCC-Ganpan";
  font-weight: 600;
  color: var(--purple);
}
</style>
