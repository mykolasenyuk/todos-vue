<template>
  <li>
    <span v-bind:class="{ done: todo.done }">
      <input type="checkbox" v-on:change="todo.done = !todo.done" />
      <strong>{{ index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button class="btn" v-on:click="$emit('dlt-todo', todo.id)">&times</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
}
</script>
<style scoped>
li {
  font-weight: normal;

  border: 1px solid #2c3e50;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 20px 10px;
}
input {
  margin-right: 1rem;
}
.btn {
  background: brown;
  border-radius: 50%;
  color: aqua;
  font-weight: bold;
  border: 1px solid red;
}
.done {
  text-decoration: line-through;
}
</style>
