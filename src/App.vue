<template>
  <div class="card">
    <h1>Todo list</h1>
    <input
      v-model="input"
      @keypress.enter="addTodo"
      type="text"
      placeholder="New todo"
    />

    <div v-for="(todo, i) in todos" :key="i" class="todo">
      <span> {{ todo }}</span>
      <button @click="removeTodo(i)">Remove</button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    input: "",
    todos: [],
  }),

  methods: {
    addTodo() {
      this.todos.push(this.input);
      this.input = "";
    },

    removeTodo(i) {
      this.todos.splice(i, 1);
    },
  },
};
</script>

<style scoped>
.card {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-width: 300px;
  max-width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

input {
  height: 3em;
  width: 100%;
  padding: 0 1em;
}

.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 0 1em;
  margin: 0.5em 0;
  border: 1px solid #ccc;
  height: 3em;
}
</style>