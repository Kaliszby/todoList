<template>
  <div>
    <div v-for="value in todoItems" v-bind:key="value.title">
      <div>
        {{ value.title }}
        <button v-on:click="deleteTodo(value)">del</button>
      </div>
    </div>
    <form @submit.prevent="createTodo">
      <div>
        <input
          v-model="newTodo"
          type="text"
          placeholder="What do you need to do today?"
        />
        <button id="add-task">Create</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      todoItems: [],
      newTodo: null,
    };
  },
  watch: {
    todoItems: {
      handler() {
        localStorage.setItem("todoItems", JSON.stringify(this.todoItems));
      },
      deep: true,
    },
  },
  mounted() {
    // console.log(localStorage.todoItems)
    if (localStorage.todoItems) {
      this.todoItems = JSON.parse(localStorage.todoItems);
    }
  },
  methods: {
    createTodo() {
      if (!this.newTodo == "") {
        this.todoItems.push({
          title: this.newTodo,
        });
        this.newTodo = "";
        console.log(this.todoItems);
      }
    },
    deleteTodo(todoItems) {
      console.log(this.todoItems.indexOf(todoItems));
      const TodoItemsIndex = this.todoItems.indexOf(todoItems);
      this.todoItems.splice(TodoItemsIndex, 1);
    },
  },
};
</script>

<style></style>
