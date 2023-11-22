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
  </Layout>
  <!-- <input
    v-model="newTodo"
    @keyup.enter="addTodo"
    placeholder="Add a new todo"
    class="input"
  />
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      {{ todo }}
      <button @click="removeTodo(index)">Remove</button>
    </li>
  </ul> -->
</template>

<script>
import Scheduler from "./components/Scheduler.vue";
import Header from "./components/Header.vue";
import Layout from "./components/Layout.vue";
import List from "./components/List.vue";

export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push(this.newTodo);
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
  components: { Scheduler, Header, Layout, List },
};
</script>

<style></style>
