<template>
  <div>
    <h2>Todos List</h2>
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter" >
      <option value="all">All</option>
      <option value="done">Done</option>
      <option value="ready">Ready to</option>

    </select>
    <hr />
    <Loader v-if="loading"/>
    <TodoList v-bind:todos="todos"
              @dlt-todo="dltTodo"
              v-else-if="filteredTodos.length"
    />
    <p v-else>Empty list</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'

export default {
  name: 'App',
  data() {
    return {
      loading:true,
      todos: [],
      filter: 'all'
    }
  },
  mounted() {
    setTimeout(()=>{
      this.todos=[
        { id: 1, title: 'buy water', done: false },
        { id: 2, title: 'take shower', done: false },
        { id: 3, title: 'drink tea', done: false },
      ]
      this.loading=false
    },1000)
  },
  computed:{
    filteredTodos(){
      if (this.filter==='done'){
        return this.todos.filter(t=>t.done)
      }
      if (this.filter==='all'){
        return this.todos
      }

      if (this.filter==='ready'){
        return this.todos.filter(t=>!t.done)
      }
    }
  },
  watch:{
    filter(value){
      console.log(value)
    }
  },
  methods: {
    dltTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    },
  },
  components: {
    TodoList,
    AddTodo,
    Loader
  },
}
</script>
