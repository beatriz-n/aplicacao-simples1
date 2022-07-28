<template>
<div class="container grid-xs py-2 ">
  <img class="img-responsive img" alt="Vue logo" src="./assets/logo.png"><br>
  <div>Esta é uma pagina usando spectre</div><br>
  <form @submit.prevent="addTodo(todo)">
    <div class="input-group">
      <input type="text" v-model="todo.description" class="form-input" placeholder="Nova tarefa">
      <button class="btn btn-primary input-group-btn">Adicionar</button>
    </div>
     <div class="todo-list">
        <todo v-for="t in todos" :key="t.id" :todo="t"/>
     </div>
  </form>
</div>
</template>

<script>
import todo from './components/todo-temp'

export default {
  name: 'app',
  components: { todo },
  data () {
    return { todos: [], todo: { checked: false } }
  },
  methods: {
    addTodo (todo) {
      todo.id = Date.now()
      this.todos.push(todo)
      this.todo = { checked: false }
    }
  }
}
</script>

<style scoped>
.img{
max-width: 200px;
margin: 0 auto;
}
.todo-list{

}
</style>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
