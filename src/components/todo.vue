<template lang="pug">

  .todo
    todoinput(
      @addTodo="addNewTodo"
    )
    todoList(
      :todos="todos"
      @checkTodo="checkTodo"
      @removeTodo="removeTodo"
    )

</template>

<script>
import todoinput from './todoinput'
import todoList from './todoList'

export default {
  data() {
    return{
      todos: []
    }
  },
  methods: {
    addNewTodo(todo) {
      this.todos.push(todo)
    },
    checkTodo(todo) {
      this.todos = this.todos.map(item => item.id === todo.id ? todo : item)
    },
    removeTodo(todoID) {
      this.todos = this.todos.filter(item => item.id !== todoID)
    }
  },
  components: {
    todoinput, todoList
  }
}
</script>

<style lang="scss" scoped>
  .todo {
    width: 100%;
  }
</style>