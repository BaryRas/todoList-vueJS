<template>
  <div class="todo-item" :class="{ isCompleted: todo.completed }">
    <input type="checkbox" @change="markCompleted" />
    <p>{{ todo.title }}</p>
    <button @click="$emit('delTodo', todo.id)">X</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  methods: {
    markCompleted() {
      this.todo.completed = !this.todo.completed;
    }
  },
  props: ["todo"]
};
</script>

<style scoped>
.todo-item {
  display: flex;
  color: #333;
  align-items: center;
  border-bottom: 1px solid #333;
  padding: 5px;
}
input {
  margin-right: 5px;
}
button {
  margin-left: auto;
  padding: 0 10px;
  background-color: red;
  color: antiquewhite;
  border: none;
  border-radius: 100px;
  cursor: pointer;
}

.isCompleted p {
  text-decoration: line-through;
}
</style>
