<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, i) of todos"
        v-bind:index="i"
        v-bind:todo="todo"
        v-on:dlt-todo="dltTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
  components: {
    TodoItem,
  },
  methods: {
    dltTodo(id) {
      this.$emit('dlt-todo', id)
    },
  },
}
</script>
<style scoped>
ul {
  list-style: none;
  font-weight: normal;
  margin: 0;
  padding: 0;
}
</style>
