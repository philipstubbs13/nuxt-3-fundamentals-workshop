<script>
import { defineNuxtComponent } from "#app";

export default defineNuxtComponent({
  data: () => ({
    todoList: [],
  }),
  methods: {
    fetchTodoList() {
      fetch("https://jsonplaceholder.typicode.com/todos/")
        .then((response) => response.json())
        .then((json) => {
          this.todoList = json;
        });
    },
  },
});
</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <img src="/todo.jpg" alt="Todo photo" width="600" />
    <h1>Hello Frontend Masters!</h1>
    <button @click="fetchTodoList">Fetch Data</button>
    <ul>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>
