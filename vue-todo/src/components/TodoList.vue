<template>
  <div>
    <ul>
      <!-- Item 삭제 시 삭제 버튼을 클릭한 index의 item만 삭제하기 위해 수정 -->
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
        <i class="fas fa-check checkBtn" v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleComplete(todoItem, index)"></i>
        <!-- <li v-for="todoItem in todoItems" v-bind:key="todoItem" class="shadow"> -->
        <!-- 객체에서 원하는 item만 가지고 와서 적용 -->
        <span v-bind:class="{ textCompleted: todoItem.completed }">
          {{ todoItem.item }}
        </span>
        <!-- v-for에서 가져온 파라미터를 removeTodo로 넘김 -->
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          <i class="fas fa-trash-alt"></i>
        </span>
        <!-- <button v-on:click="removeTodo"></button> -->
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: [
    'propsdata'
  ],
  methods: {
    removeTodo: function (todoItem, index) {
      console.log(todoItem, index);
      // localStorage에 저장할 때 key, value를 동일하게 저장했음
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    toggleComplete: function (todoItem, index) {
      // console.log(todoItem);
      todoItem.completed = !todoItem.completed;
      // localStorage를 자동으로 updata를 할 수 없음 - 로컬 스토리지에 데이터 갱신
      localStorage.removeItem(todoItem.item);
      localStorage.setItme(todoItem.item, JSON.stringify(todoItem));
    }
  },

};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0px;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background-color: #fff;
  border-radius: 5px;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
  cursor: pointer;
}

.checkBtnCompleted {
  color: #b3adad;
}

.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
  cursor: pointer;
}
</style>
