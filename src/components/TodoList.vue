<template>
  <div>
    <ul v-if="this.todos.length > 0">
      <li
        v-for="todo in this.todos"
        :key="todo.id"
        :class="{ completed: todo.completed }"
        @click="this.toggleComplete(todo.id)"
      >
        <i @click="this.deleteTodo(todo.id)" v-show="todo.completed">X</i>
        {{ todo.title }}
      </li>
    </ul>

    <p v-else>Yeey No Task to Do</p>
  </div>
</template>

<script>
export default {
  props: {
    todos: Array,
    toggleComplete: Function,
    deleteTodo: Function,
  },
};
</script>

<style lang="scss" scoped>
div {
  width: 100%;
  ul {
    list-style: none;
    height: 40vh;
    overflow: auto;
    li {
      font-size: 1.4rem;
      cursor: pointer;
      border-bottom: 1px solid var(--color-muted);
      word-wrap: break-word;

      &.completed {
        text-decoration: line-through dotted;
      }
      i {
        color: var(--color-danger);
        font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
          "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
        font-weight: 900;
      }
    }
  }
  p {
    font-size: 2rem;
    &::before,
    &::after {
      content: "\1F38A";
    }
  }
}
</style>
