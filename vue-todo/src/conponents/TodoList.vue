<template>
  <div>
    <ul>
      <!-- Item 삭제 시 삭제 버튼을 클릭한 index의 item만 삭제하기 위해 수정 -->
      <li
        v-for="(todoItem, index) in todoItems"
        v-bind:key="todoItem"
        class="shadow"
      >
        <!-- <li v-for="todoItem in todoItems" v-bind:key="todoItem" class="shadow"> -->
        {{ todoItem }}
        <!-- v-for에서 가져온 파라미터를 removeTodo로 넘김 -->
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)"
          ><i class="fas fa-trash-alt"></i
        ></span>
        <!-- <button v-on:click="removeTodo"></button> -->
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todoItems: []
    };
  },
  methods: {
    removeTodo: function(todoItem, index) {
      console.log(todoItem, index);
      // localStorage에 저장할 때 key, value를 동일하게 저장했음
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },
  created: function() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          this.todoItems.push(localStorage.key(i));
          console.log(localStorage.key(i));
        }
      }
    }
    // console.log("created");
  }
};
</script>

<style>
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
}
.checkBtnComplated {
  color: #b3adad;
}
.textComplated {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
  cursor: pointer;
}
</style>
