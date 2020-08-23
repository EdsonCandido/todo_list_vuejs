<template>
  <div class="" id="app">
    <div class="container grid-xs p-2">
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input
            type="text"
            v-model="todo.description"
            class="form-input"
            placeholder="New Todo"
          />
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <Todo v-for="t in todos" :key="t.id" :todo="t" />
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./components/Todo";
export default {
  name: "App",
  components: { Todo },
  data() {
    return { todos: [], todo: { checked: false } };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
    }
  }
};
</script>

<style>
.todo-list {
  padding-top: 2rem;
}
</style>
