<template>
  <button class="button" @click="handleClick"><slot></slot></button>
</template>
<script>
export default {
  methods: {
    handleClick() {
      console.log("button in components");
      // this.$emit("click");
    },
  },
};
</script>

<style scoped>
.button {
  min-width: 40px;
  height: 40px;
  border-radius: 8px;
  background-color: orange;
  color: white;
  font-size: 24px;
  font-weight: bold;
  cursor: pointer;
  outline: none;
  border: 0;
  box-sizing: border-box;
}
.button:hover {
  opacity: 0.8;
}
</style>
