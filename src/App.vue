<!-- App.vue -->
<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #scheduler>
      <Scheduler />
    </template>
    <template #list>
      <List />
    </template>
    <template #floating-button>
      <FloatingButton />
    </template>
  </Layout>
</template>

<script>
import Scheduler from "./components/Scheduler.vue";
import Header from "./components/Header.vue";
import Layout from "./components/Layout.vue";
import List from "./components/List.vue";
import Modal from "./components/Modal.vue";
import { ref, provide } from "vue";
import { listItemData } from "../data";
import FloatingButton from "./components/FloatingButton.vue";
import dayjs from "dayjs";

export default {
  setup() {
    const selectedDate = ref(dayjs().format("YYYY-MM-DD"));
    provide("selectedDate", selectedDate);
    const initialListItemData = ref(listItemData);
    provide("initialListItemData", initialListItemData);

    const listItem = ref(initialListItemData.value);
    provide("listItem", listItem);

    const onDayClickHandler = (date) => {
      selectedDate.value = date.id;
      const listItemByDate = initialListItemData.value.filter(
        (item) => item.date === date.id
      );
      listItem.value = listItemByDate;
    };
    provide("onDayClickHandler", onDayClickHandler);

    const isModalVisible = ref(false);

    function showModal() {
      isModalVisible.value = true;
    }
    function closeModal() {
      isModalVisible.value = false;
    }

    function addTodo(title, content, priority) {
      if (title.trim() !== "" && content.trim() !== "") {
        const submitData = {
          title: title,
          content: content,
          date: selectedDate.value,
          status: "todo",
          priority: priority,
        };
        listItem.value.unshift(submitData);
        initialListItemData.value.unshift(submitData);

        closeModal();
      }
    }

    provide("addTodo", addTodo);
    provide("isModalVisible", isModalVisible);
    provide("showModal", showModal);
    provide("closeModal", closeModal);
  },

  components: { Scheduler, Header, Layout, List, Modal, FloatingButton },
};
</script>

<style></style>
