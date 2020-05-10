<template lang="html">
  <div class="clearAllContainer">
    <span class="clearAllBtn" v-on:click="clearTodo">모두삭제</span>
  </div>
</template>

<script>
export default {
  methods : {
    clearTodo : function(){
      this.$emit("clearTodo");
    }
  }
}
</script>

<style lang="css" scoped>
  .clearAllContainer{
    width : 8.5rem;
    height : 50px;
    line-height: 50px;
    background-color : white;
    border-radius : 5px;
    margin : 0 auto;
  }

  .clearAllBtn {
    color : #e20303;
    display : black;
  }
</style>
