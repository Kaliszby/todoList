<template>
  <div id="app"><todoList /></div>
</template>

<script>
import todoList from "../src/components/todoList.vue";

export default {
  name: "app",
  components: {
    todoList,
  },
  data() {
    return {
      item: null,
    };
  },
  methods: {
    createTodoList() {
      alert(this.item);
    },
  },
};
</script>

<style></style>
