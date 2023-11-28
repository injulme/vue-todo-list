<template>
  <div class="list-item" @click="changeStatus(status)">
    <div
      class="list-item__status-icon"
      :class="{ 'todo-icon': status === 'todo' }"
    >
      <component :is="iconComponent" />
    </div>
    <div>
      <div class="list-item__title">
        {{ title }}
      </div>
      <div class="list-item__content">
        {{ content }}
      </div>
    </div>
  </div>
</template>

<script>
import CheckCircleIcon from "./icons/IconCheckCircle.vue";

export default {
  props: {
    title: String,
    content: String,
    date: String,
    status: String,
    index: Number,
  },

  methods: {
    changeStatus(status) {
      let newStatus = "";
      if (status === "todo") newStatus = "success";
      else if (status === "success") newStatus = "todo";
      else alert("잘못된 접근입니다.");

      this.$emit("updateStatus", newStatus, this.index);
    },
  },
  computed: {
    iconComponent() {
      return CheckCircleIcon;
    },
  },
};
</script>

<style>
.list-item {
  background-color: var(--purple-light);
  border-radius: var(--border-radius-sm);
  display: flex;
  gap: 12px;
  padding: 12px;
  align-items: center;
  cursor: pointer;
}
.list-item:hover {
  background-color: var(--blue-light);
}
.list-item__status-icon {
  width: 32px;
  height: 32px;
}
.list-item__status-icon svg {
  width: 32px;
  height: 32px;
  fill: var(--purple-dark);
}

.todo-icon svg {
  fill: var(--gray);
}
.list-item__title {
  font-size: 14px;
}
.list-item__content {
  font-size: 20px;
}
</style>
