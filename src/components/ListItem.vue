<template>
  <div class="list-item">
    <div class="list-item__status-icon">
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
const statusIcons = {
  todo: XmarkCircleIcon,
  inprogress: CheckCircleIcon,
  success: CheckCircleIcon,
};
import CheckCircleIcon from "./icons/IconCheckCircle.vue";
import XmarkCircleIcon from "./icons/IconXmarkCircle.vue";
export default {
  props: ["title", "content", "date", "status"],

  computed: {
    iconComponent() {
      return statusIcons[this.status];
    },
  },
};
</script>

<style>
.list-item {
  background-color: var(--coral-light);
  border-radius: var(--border-radius-sm);
  display: flex;
  gap: 12px;
  padding: 12px;
  align-items: center;
}
.list-item__status-icon {
  width: 32px;
  height: 32px;
}
.list-item__status-icon svg {
  width: 32px;
  height: 32px;
  fill: var(--purple);
}
.list-item__title {
  font-size: 14px;
}
.list-item__content {
  font-size: 20px;
}
</style>
