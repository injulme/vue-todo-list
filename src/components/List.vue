<template>
  <div class="list">
    <ListItem
      v-for="(item, index) of listItem"
      :title="item.title"
      :content="item.content"
      :date="item.date"
      :status.sync="item.status"
      @updateStatus="updateStatus"
      :index="index"
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
          content: "대기중인 공부하기",
          date: "2023-11-23T09:00:00.000Z",
          status: "todo",
        },
        {
          title: "할일 3",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 4",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 5",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "todo",
        },
        {
          title: "할일 6",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 7",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 8",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 9",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
        {
          title: "할일 10",
          content: "완료된 머리 자르기",
          date: "2023-11-21T09:00:00.000Z",
          status: "success",
        },
      ],
    };
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
  margin: 20px 0;
  /* border: 1px solid rebeccapurple; */
  height: 400px;
  overflow: auto;
  scrollbar-width: none;
  scroll-behavior: smooth;
}
.list::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera*/
  scroll-behavior: smooth;
}
</style>
