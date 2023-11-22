<template>
  <div class="list">
    <ListItem
      v-for="item of listItem"
      :title="item.title"
      :content="item.content"
      :date="item.date"
      :status="item.status"
    />
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
export default {
  data() {
    return {
      listItem: [
        {
          title: "할일 1",
          content: "대기중인 병원가기",
          date: "2023-11-22T09:00:00.000Z",
          status: "todo",
        },
        {
          title: "할일 2",
          content: "진행중인 공부하기",
          date: "2023-11-23T09:00:00.000Z",
          status: "inprogress",
        },
        {
          title: "할일 3",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
      ],
    };
  },
  // props: {
  //   listItem: ["item1", "item2", "item3"],
  // },
  components: { ListItem },
};
</script>

<style>
.list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin: 20px 0;
}
</style>
