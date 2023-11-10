<script setup>
const props = defineProps({
  text: String,
  variant: "primary" | "secondary",
});
console.log("props => ", props.variant);
</script>

<template>
  <button class="button">{{ text }}</button>
</template>

<style scoped>
button {
  padding: 12px 24px;
  border: 2px solid yellow;
  border-radius: 8px;
  background-color: orange;
  color: white;
  font-size: 24px;
  font-weight: bold;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
</style>
