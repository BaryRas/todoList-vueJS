<template>
  <div id="app">
    <Header />
    <AddTodos @addTodo="addTodo" />
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" @delTodo="delTodo" />
    </div>
    <!-- <template>
      <ul>
        <li v-for="todo in todos" :key="todo.id">{{ todo.title }}</li>
      </ul>
    </template> -->
  </div>
</template>

<script>
import Header from "./components/Header.vue"; // AddTodo TodoItem
import AddTodos from "./components/AddTodos.vue";
import TodoItem from "./components/TodoItem.vue";

export default {
  name: "app",
  data() {
    return {
      todos: [
        {
          userId: 1,
          id: 1,
          title: "delectus aut autem",
          completed: false
        },
        {
          userId: 1,
          id: 2,
          title: "quis ut nam facilis et officia qui",
          completed: false
        },
        {
          userId: 1,
          id: 3,
          title: "fugiat veniam minus",
          completed: false
        },
        {
          userId: 1,
          id: 4,
          title: "et porro tempora",
          completed: false
        }
      ]
    };
  },
  components: {
    Header,
    AddTodos,
    TodoItem
  },
  methods: {
    delTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newtodo) {
      this.todos = [...this.todos, newtodo];
    }
  }
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  /* text-align: center; */
  /* color: #2c3e50; */
}
</style>
