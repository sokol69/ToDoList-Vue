<template lang="pug">

  .app
    todo

</template>

<script>
import todo from './components/todo'

export default {
  components: {
    todo
  }
}
</script>

<style lang="scss" scoped>
  .app {
    width: 50%;
    margin: 100px auto;
    display: flex;
    justify-content: center;
    text-align: center;
  }
</style>
