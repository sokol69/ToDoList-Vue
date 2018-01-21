<template lang="pug">

  .todo-input
    input(
      type="text",
      placeholder="+ Добавить задачу...",
      v-model="todo.name"
      @keydown.enter="addTodo"
    ).input

</template>

<script>
let uniqId = 1;
export default {
  data() {
    return {
      todo: {
      id: 0,
      name: '',
      checked: false
      }
    };
  },
  methods: {
    addTodo() {
      this.todo.id = uniqId++;
      this.$emit('addTodo', {...this.todo});
      this.todo.name = '';
    }
  }
}
</script>

<style lang="scss" scoped>
  .todo-input {
    width: 100%;
  }
  .input {
    width: 100%;
    height: 50px;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
    background: #73A6C1;
    color: white;
  }
::-webkit-input-placeholder {color:#fff;}
::-moz-placeholder          {color:#fff;}
:-moz-placeholder           {color:#fff;}
:-ms-input-placeholder      {color:#fff;}
</style>
