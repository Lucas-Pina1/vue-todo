<template>
  <div id="app">
    <div class="container grid-xs py-2">
      <img
        class="img-responsive img-logo"
        src="./assets/logo.png"
        alt="logo marca"
      />
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input
            type="text"
            v-model="todo.description"
            class="form-input"
            placeholder="Novo todo"
          />
          <button class="btn btn-primary input-group btn">Adicionar</button>
        </div>
        <div class="todo-list">
          <new-todo
            v-for="task in todos"
            :key="task.id"
            @toggle="toggleTodo"
            @remove="removeTodo"
            :todo="task"
          ></new-todo>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import newTodo from "@/components/newTodo.vue";

export default {
  name: "app",
  components: {
    newTodo,
  },
  data() {
    return {
      todos: [],
      todo: {
        checked: false,
      },
    };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
    },
    toggleTodo(todo) {
      const index = this.todos.findIndex((item) => item.id === todo.id);
      if (index > -1) {
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, { ...this.todos[index], checked });
      }
    },
    removeTodo(todo) {
      const index = this.todos.findIndex((item) => item.id === todo.id);
      if (index > -1) {
        this.$delete(this.todos, index);
      }
    },
  },
};
</script>

<style scoped>
.todo-list {
  padding-top: 2rem;
}
</style>
