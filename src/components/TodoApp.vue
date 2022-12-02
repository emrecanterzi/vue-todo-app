<script setup>
import AddTodoForm from "./AddTodoForm.vue";
import TodoList from "./TodoList.vue";
</script>

<template>
  <main class="container">
    <h1>Todo App</h1>
    <AddTodoForm :addTodo="this.addTodo" />
    <TodoList
      :todos="this.todos"
      :toggleComplete="this.toggleComplete"
      :deleteTodo="this.deleteTodo"
    />
    <button @click="this.deleteAllCompletedTodos">Clear Completed!</button>
  </main>
</template>

<script>
export default {
  components: { TodoList, AddTodoForm },
  data() {
    return {
      todos: [],
    };
  },

  methods: {
    addTodo: function (title, description) {
      this.todos.push({ id: Date.now(), title });
    },
    toggleComplete: function (todoId) {
      this.todos = this.todos.map((todo) =>
        todo.id == todoId ? { ...todo, completed: !todo.completed } : todo
      );
    },
    deleteTodo: function (todoId) {
      this.todos = this.todos.filter((todo) => todo.id != todoId);
    },
    deleteAllCompletedTodos: function () {
      this.todos = this.todos.filter((todo) => !todo.completed);
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  margin: 0 auto;
  min-height: 100vh;
  width: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;

  h1 {
    text-shadow: 0.5rem 0.5rem 0.3rem var(--color-muted);
  }

  button {
    font-size: 1.2rem;
    background-color: var(--color-muted);
    border: none;
    padding: 0.3rem 0.5rem;
    margin: 0.2rem 0;
    cursor: pointer;
    color: var(--color-dark);
    outline: 1px solid var(--color-muted);
    transition: 0.3s;

    &:hover {
      background-color: var(--color-dark);
      color: var(--color-muted);
    }
  }
}
</style>
