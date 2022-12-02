<template>
  <form @submit="this.submitHandler">
    <div>
      <label for="title">Title</label>
      <input
        type="text"
        name="title"
        id="title"
        :value="this.title"
        @input="this.changeHandler"
        autocomplete="off"
      />
    </div>
    <button>Add Todo</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  props: {
    addTodo: Function,
  },

  methods: {
    submitHandler(e) {
      e.preventDefault();
      if (!!this.title.trim()) this.addTodo(this.title);
      else title.setAttribute("errored", true);

      this.title = "";
    },
    changeHandler(e) {
      this.title = e.target.value;
      title.setAttribute("errored", false);
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  display: flex;
  flex-direction: column;
  width: 100%;

  div {
    display: flex;
    flex-direction: column;
    label {
      font-size: 1.2rem;
    }
    input {
      font-size: 1.2rem;
      background-color: transparent;
      border: none;
      padding: 0.3rem 0.5rem;
      outline: 1px solid var(--color-muted);
      color: var(--color-muted);
      transition: 0.3s;

      &[errored="true"] {
        background-color: var(--color-danger);
      }
    }
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
