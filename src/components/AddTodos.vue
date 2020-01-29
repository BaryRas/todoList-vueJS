<template>
  <div>
    <form class="add-todo" @submit.stop.prevent="addTodo">
      <input
        type="text"
        placeholder="Add Todos..."
        v-model="title"
        name="title"
      />
      <button type="submit" value="Submit">Submit</button>
    </form>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodos",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const uid = uuid.v4();
      const newTodo = {
        id: uid,
        userId: uid,
        title: this.title,
        completed: false
      };
      // send up to parent
      this.$emit("addTodo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style scoped>
.add-todo {
  display: flex;
  margin-bottom: 5px;
}
input {
  flex: 1;
  color: #333;
  padding: 5px;
}
button {
  padding: 0 10px;
  background-color: #333;
  color: antiquewhite;
  border: none;
  cursor: pointer;
}
</style>
