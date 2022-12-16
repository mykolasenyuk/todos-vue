<template>
  <div>
    <h2>Todos List</h2>
    <AddTodo @add-todo="addTodo" />
    <hr />
    <TodoList v-bind:todos="todos" @dlt-todo="dltTodo" />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        { id: 1, title: 'buy water', done: false },
        { id: 2, title: 'take shower', done: false },
        { id: 3, title: 'drink tea', done: false },
      ],
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
  },
}
</script>
