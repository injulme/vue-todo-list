<template>
  <div class="list-container">
    <input class="list-input" />
    <Button @click="callAlert"> + </Button>
  </div>
</template>
<script>
import Button from "./Button.vue";

export default {
  components: {
    Button,
  },
  methods: {
    callAlert() {
      console.log("click me");
    },
  },
};
</script>

<style scoped>
.list-container {
  width: 450px;
  height: 800px;
  border: 1px solid white;
  border-radius: 4px;
  display: flex;
  gap: 12px;
  padding: 12px;
  background-color: white;
}

.list-input {
  height: 40px;
  width: 100%;
  font-size: 24px;
}
</style>
