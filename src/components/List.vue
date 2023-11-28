<template>
  <div class="list">
    <ListItem
      v-if="listItem.length > 0"
      v-for="(item, index) of listItem"
      :title="item.title"
      :content="item.content"
      :date="item.date"
      :status.sync="item.status"
      :priority="item.priority"
      @updateStatus="updateStatus"
      :index="index"
      :key="`${item.title}_${index}`"
    />
    <div v-else>등록된 일정이 없습니다.</div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
import { inject, isProxy, toRaw } from "vue";

export default {
  setup() {
    const listItem = inject("listItem");
    const initialListItemData = inject("initialListItemData");
    const selectedDate = inject("selectedDate");

    let listByDate = initialListItemData.value;
    if (isProxy(listByDate)) {
      listByDate = toRaw(initialListItemData.value).filter(
        (item) => item.date === selectedDate.value
      );
    }

    listItem.value = listByDate;

    return { listItem };
  },
  methods: {
    updateStatus(status, index) {
      let item = this.listItem[index];
      item.status = status;
    },
  },

  components: { ListItem },
};
</script>

<style>
.list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding-bottom: 80px;
  margin: 20px 0;
  height: 400px;
  overflow: auto;
  scrollbar-width: none;
  scroll-behavior: smooth;
}
.list::-webkit-scrollbar {
  display: none;
  scroll-behavior: smooth;
}
</style>
