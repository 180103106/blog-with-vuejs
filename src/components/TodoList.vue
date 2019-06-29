<template>
  <div>
    <div v-for='(todo, index) in todoList' v-bind:key = 'index'  >
        <div  class = "box" v-bind:class="{ done: todo.done }" v-show="todoId == index + 1">
          <p>New page</p>
          <div v-if="titleText || descText">
            <h1>{{titleText}}</h1>
            <h3>{{descText}}</h3>
          </div>
          <div v-else>
            <h1 >{{todo.title}}</h1>
          <h3>{{todo.description}}</h3>
          </div>
          
          <div>
            <form >
              <div class="field">
                <label>Title</label>
                <input v-model="titleText" type="text" ref="title" defaultValue="">
              </div>
              <div class="field">
                <label>desc</label>
                <input v-model="descText" type="text" ref="description" defaultValue="">
              </div>
              <div class="buttons">
                <button class="btn" @click="edit(index)">Edit Blog</button>
                <button class="btn" v-on:click="remove">Delete Blog</button>
              </div>
            </form>
        </div>
        </div>
       
    </div>
    
  </div>
</template>

<script>
  export default {
      name: "TodoList",
      data() {
        return {
          todoId: this.$route.params.index,
          todoList: JSON.parse(localStorage.getItem('todolist')),
          titleText: "",
          descText: "",
        
        }
      },
      methods: {
        edit(index) {
          if (this.titleText.length > 0 && this.descText.length > 0) {
            
            const title = this.titleText
            const description = this.descText
            const done = this.todoList[index].done
            const temp =  { 'title' : title, 'description' : description, done: done };

            this.todoList[index] = temp;
            localStorage.setItem('todolist', JSON.stringify(this.todoList));
          }
        },
        remove(index){
          this.todoList.splice(index, 1);
          const parsed = JSON.stringify(this.todoList);
          localStorage.setItem('todolist', parsed);
        }
  }
  }
</script>

<style>
  .box.done {
        background-color: orangered;
        border: none;
        box-shadow: 0px 10px 30px rgba(orangered,0.4)
  }
</style>
