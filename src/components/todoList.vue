<template lang="pug">
  .todo-list(v-if="todos.length")
    .content
      ul.list
        li.item(v-for="todo in filteredItems")
          todoItem(
            :todo="todo"
            @checkTodo="checkTodo"
            @removeTodo="removeTodo"
          )
    .footer
      .footer-content
        .counter
          | Количество задач: {{todos.length}}
        .filter
          button(type="button" @click="applyFilter('all')" :class="{active: filter === 'all'}") Все
          button(type="button" @click="applyFilter('active')" :class="{active: filter === 'active'}") Активные
          button(type="button" @click="applyFilter('completed')" :class="{active: filter === 'completed'}") Завершенные
</template>

<script>
import todoItem from './todoItem'
export default {
  props: {
    todos: Array
  },
  data() {
    return {
      filter: 'all'
    }
  },
  computed: {
    filteredItems() {
      switch(this.filter) {
        case 'all':
          return this.todos
        case 'active':
          return this.todos.filter(item => !item.checked)
        case 'completed':
          return this.todos.filter(item => item.checked)
      }
    }
  },
  methods: {
    checkTodo(todo) {
      this.$emit('checkTodo', todo);
    },
    removeTodo(todoID) {
      this.$emit('removeTodo', todoID)
    },
    applyFilter(filterName) {
      this.filter = filterName
    }
  },
  components: {
    todoItem
  }
}
</script>

<style lang="scss" scoped>
  .filter{
    display: flex;
    justify-content: space-around;
    margin: 30px 10px 10px 10px;
  }
  button {
    color: white;
    background: #73A6C1;
    border: 0;
    border-radius: 5px;
    cursor: pointer;
  }
  .counter {
    color: white;
  }
  .footer {
    background: #73A6C1;
    border-radius: 5px;
    margin: 10px 0;
    display: flex;
    justify-content: center;
    height: 100px;
  }
  .footer-content {
    width: 90%;
    margin: 15px;
  }
</style>

