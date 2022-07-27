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
        <div class="tile flex-centered" v-for="t in todos" :key="t.id">
          <div class="tile-icon">
            <div>
            <i class="icon icon-time "></i>
            </div>
          </div>
        <dir class="tile-content">
          <div class="tile-subtitle">{{t.description}}</div>
        </dir>
        <div class="tile-action">
          <button class="btn btn-link">Concluir</button>
          <button class="btn btn-link">
            <span class="text-error">Remover</span>
          </button>
          </div>
        </div>
     </div>
  </form>
</div>
</template>

<script>
export default {
  name: 'app',
  components: {},
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
