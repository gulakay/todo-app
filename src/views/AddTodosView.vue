<template>
  <div>
    <h3>Gül's Todos</h3>
    <form @submit.prevent="addTodo">
      <div class="input-container">
        <input type="text" v-model="todo" placeholder="Add Todo" />
        <button type="submit">Add</button>
      </div>
    </form>
    <div>
      <h3>Todos</h3>
      <div v-for="todo in todos" :key="todo.id">
        <p :class="{ done: todo.done }" @click="done(todo)">
          {{ todo.content }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const todo = ref("");
    const todos = ref([]);

    const addTodo = () => {
      todos.value.push({
        done: false,
        content: todo.value,
        id: Date.now(),
      });
      todo.value = "";
    };

    const done = (todo) => {
      todo.done = !todo.done;
    };

    return { todo, todos, addTodo, done };
  },
};
</script>

<style>
.input-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

input {
  width: 500px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  outline: none;
  margin-right: 10px;
}

button {
  padding: 10px 20px;
  background-color: #686868;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}
p {
  color: #686868;
  font-size: 16px;
}
p:hover {
  color: #5d1b7d;
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}

button:hover {
  background-color: #5d1b7d;
}
</style>
