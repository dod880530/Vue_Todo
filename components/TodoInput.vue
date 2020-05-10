<template lang="html">
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="새로운 할 일" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
    <modal v-if="showModal" v-on:close="showModal=false">
      <h3 slot="header">경고</h3>
      <span slot="footer" v-on:click="showModal=false">
        할 일을 입력하세요.
        <i class="closeModalBtn fa fa-times" aria-hidden="ture"></i>
      </span>
    </modal>
  </div>
</template>

<script>
import Modal from "./Modal.vue";
export default {
  components : {
    Modal : Modal
  },
  data() {
    return {
      newTodoItem : "",
      showModal : false
    }
  },

  methods : {
    addTodo : function() {
      if(this.newTodoItem !== ""){
        //예외처리 : 값이 있을 경우에만 value에 저장, 공백제거
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      }
      else{
        this.showModal = !this.showModal;
      }
    },
  }
}
</script>

<style lang="css" scoped>
  input:focus {
    outline : none;
  }

  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 10px;
  }

  .inputBox input {
    border-style : none;
    font-size : 1.2rem;
  }

  .addContainer {
    float : right;
    background : linear-gradient(to right, #4e7cff, #5afff0);
    display : inline-block;
    width : 3rem;
    border-radius: 0 5px 5px 0;
  }

  .addBtn {
    color : white;
    vertical-align: middle;
  }
</style>
