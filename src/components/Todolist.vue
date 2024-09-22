<template>
  <div>
    <h1>Todo List</h1>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.text }}
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        { text: 'Learn Vue' },
        { text: 'Build a Todo App' }
      ],
      newTodo: ''
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
input {
  margin-top: 10px;
}
button {
  margin-left: 10px;
  color: red;
  cursor: pointer;
}
</style>