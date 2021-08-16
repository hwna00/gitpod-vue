<template>
  <div>
    <h2>TODO LIST</h2>
    <div class="input">
      <input type="text" v-model="input">
      <button @click="addTodo">입력</button>
    </div>
    <TodoItem :todos="todoList"/>
  </div>
</template>

<script>
import TodoItem from '../components/TodoItem.vue';

export default {
  name: "Home",
  components: {
    TodoItem,
  },
  data() {
    return {
      input: "",
      todoList: []
    }
  },
  methods: {
    addTodo() {
      console.log('add todo!');
      this.todoList.push(this.input);
      localStorage.setItem("todos", JSON.stringify(this.todoList));
      this.input = "";
    },
    deleteTodo() {
      console.log('delete todo!');
    }
    // get => localStorage["name"]
    // remove => localStorage.removeItem("name")
    // localStorage.clear() => 전체삭제
  },
  created() {
    this.todoList = JSON.parse(localStorage.getItem("todos"))
  }
};
</script>

<style scoped>

</style>