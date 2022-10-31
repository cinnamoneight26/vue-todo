<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./conponents/TodoHeader.vue";
import TodoInput from "./conponents/TodoInput.vue";
import TodoList from "./conponents/TodoList.vue";
import TodoFooter from "./conponents/TodoFooter.vue";

export default {
  new: "#app",
  components: {
    // 컴포넌트 태금ㅇ : 컴포넌트 내용
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter
  }
};
</script>

<style></style>
