<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <input type="text" 
      v-model="newTodo"
      v-on:keyup.enter="addTodo">
    <button v-on:click="addTodo">Add</button>
    <h1>Current item is: {{ newTodo }}</h1>
    <h2>List array: {{ todoList }}</h2>
    <ol>
      <li v-for="(todo) in todoList" 
      :key="todo"
      @click="removeTodo(todo)">{{ todo }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: ()=> ({
    newTodo: '',
    todoList: ['eat','breath','fart','live','noms','code']
  }),
  methods: {
    addTodo: function() {
      this.todoList = [...this.todoList, this.newTodo];
      this.newTodo = '';
    },
    removeTodo(todo) {
      this.todoList.splice(this.todoList.indexOf(todo), 1)
    }
  }
}
</script>


<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
