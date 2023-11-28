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
import { ref, inject, isProxy, toRaw } from "vue";

const selectedDate = inject("selectedDate");
const onDayClickHandler = inject("onDayClickHandler");
const initialListItemData = inject("initialListItemData");

let initial = initialListItemData.value;
let dotDates = [];
if (isProxy(initial)) {
  initial = toRaw(initialListItemData.value);
  dotDates = initial.reduce((acc, current) => {
    if (acc.findIndex((date) => date === current.date) === -1) {
      acc.push(current.date);
    }
    return acc;
  }, []);
}

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
  {
    dot: true,
    dates: dotDates,
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

.scheduler :deep(.vc-dot) {
  background-color: var(--pink);
}
</style>
