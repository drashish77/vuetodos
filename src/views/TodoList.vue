<script>
import { ref } from "vue";
export default {
  name: "todoList",
};
</script>
<script setup>
const name = ref("Todo list in composition api");
const todoName = ref("");
const todos = ref([]);
const addTodo = () => {
  if (!todoName.value) {
    alert("Please fill the todo list");
    return;
  }
  const todo = {
    id: Date.now().toString(),
    todo: todoName.value,
  };
  todos.value.push(todo);
  todoName.value = "";

};
const deleteTodo = (id) => {
  const filteredTodos = todos.value.filter((todo) => todo.id !== id);
  todos.value = filteredTodos;
};
const deleteAllTodos = () => {
  todos.value = [];
};
</script>

<template>
  <div>
    <h1>This is a todo list</h1>
    <h3>{{ name }}</h3>
    <div class="form">
      <input
        type="text"
        v-model="todoName"
        class="form__control"
        placeholder="type here.."
      />
      <button class="btn" @click="addTodo">Add</button>
    </div>
    <div class="todos">
      <ul class="">
        <li class="" v-for="(todo, index) in todos" :key="index">
          <span>{{ todo.todo }}</span
          ><button @click="deleteTodo(todo.id)">Delete</button>
        </li>
        <hr />
      </ul>
      <button class="delete__all" @click="deleteAllTodos">Delete All</button>
    </div>
  </div>
</template>
<style scoped>
.form {
  width: 80%;
  margin: auto;
}
.form__control {
  width: 100%;
  padding: 10px 15px;
  font-size: 18px;

  outline: none;
  border: none;
  border-bottom: 1px solid #000;
}
.btn {
  padding: 10px 15px;
  margin: 10px 0;
  font-size: 18px;
  border-radius: 10px;
  background-color: cyan;
  color: black;
  cursor: pointer;
}
.btn:hover {
  background-color: darkcyan;
  color: white;
}

.todos li {
  width: 60%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
}
.todos button {
  background-color: red;
  color: white;
  border-radius: 20px;
  padding: 10px 15px;
  margin: 10px 0;
  font-size: 18px;
  border-radius: 10px;
}
</style>
