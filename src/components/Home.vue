<template>
  <div>
    <Card :todo-list="todoList" />
  </div>
</template>
<script>
  import Card from './Card';

  export default {
    name: 'Home',
    data() {
      return {
        todoList: []
      }
    },
    mounted() {
        if (localStorage.getItem('todolist')) {
          this.todoList = JSON.parse(localStorage.getItem('todolist'));
        }
    }
  }
</script>

<style>
  
</style>
