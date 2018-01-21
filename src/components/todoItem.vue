<template lang="pug">
  .todo-item(:class="{checked : todo.checked}")
    label.label
      .input-block
        input(
          type="checkbox"
          @change="checkTodo"
          :checked="todo.checked"
        ).input
        .title {{todo.name}}
        .button
          button(
            type="button"
            @click="removeTodo"
          ).remove
            | x
</template>

<script>
export default {
  props: {
    todo: Object
  },
  methods: {
    checkTodo(e) {
      const todoItem = {
        ...this.todo,
        checked: e.target.checked
      }
      this.$emit('checkTodo', todoItem)
    },
    removeTodo() {
      this.$emit('removeTodo', this.todo.id)
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-item {
  width: 100%;
  background: #fff;
  margin-bottom: 2px;
  height: 40px;
  border-radius: 5px;
}
.input-block {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 100%;
}
.label {
  width: 100%;
}
.checked {
  text-decoration: line-through;
  opacity: .5;
}
.remove {
  border: 0;
  background: #fff;
  cursor: pointer;
  color: red;
}
.input {
  margin-left: 10px;
}
</style>
