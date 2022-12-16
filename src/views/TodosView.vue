<template>
  <div>
    <h2>Todos List</h2>
    <AddTodo @add-todo="addTodo" />
    <hr />
    <Loader v-if="loading"/>
    <TodoList v-bind:todos="todos"
              @dlt-todo="dltTodo"
              v-else-if="todos.length"
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
    },1500)
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
