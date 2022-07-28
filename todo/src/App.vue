<template>
<div class="container grid-xs py-2 ">
  <img class="img-responsive img" alt="Vue logo" src="./assets/logo.png"><br>
   <div class id="app">
    <div class="container grid-xs py-2">
      <div><b>Digite lembretes:</b></div>
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo">
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>
      <div class="todo-list">
        <todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" @remove="removeTodo" :todo="t"/>
      </div>
    </div>
  </div>
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
    },

    toggleTodo (todo) {
      const index = this.todos.findIndex(item => item.id === todo.id)
      if (index > -1) {
        const checked = !this.todos[index].checked
        this.todos[index].checked = checked
      }
    },
    removeTodo (todo) {
      const index = this.todos.findIndex((item) => item.id === todo.id)

      if (index > -1) {
        this.todos.splice(index, 1)// não precisa reatribuir ao this.todos
      }// pois 'splice' já altera o array original
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
 padding-top: 2rem;
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
