<template lang="html">
  <div id="app">
    <!-- Vue인스턴스를 생성하지도 않았는데, 인스턴스가 app에 담겼다-->
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:clearTodo="clearTodo"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoList from "./components/TodoList.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoFooter from "./components/TodoFooter.vue";
export default {
  //지역컴포넌트등록
  components : {
    'TodoHeader' : TodoHeader,
    'TodoList' : TodoList,
    'TodoInput' : TodoInput,
    'TodoFooter' : TodoFooter,
  },

  //데이터를 담는
  data() {
    return {
      todoItems : [],
    }
  },

  created(){
    //?? 생성될때마다????
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },

  methods : {
    addTodo : function(value) {
      localStorage.setItem(value, value);
      this.todoItems.push(value);
    },

    clearTodo : function(){
      localStorage.clear();
      this.todoItems = [];
    },

    removeTodo : function(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1);
    }
  }

}
</script>

<style lang="css">
  body  {
    /*에플리케이션 전체 배경*/
    text-align: center;
    background-color: #f6f6f6;
  }

  input{
    /*할일 입력 input박스*/
    border-style: groove;
    width : 200px;
  }
  button{
    border-style: groove;
  }
  .shadow {
    box-shadow : 5px 10px 10px rgba(0,0,0,0.3);
  }
</style>
