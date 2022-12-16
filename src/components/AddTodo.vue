<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title" />
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: '',
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          done: false,
        }
        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    },
  },
}
</script>

<style scoped>
form {
  display: flex;
  justify-content: space-around;
  padding: 10px;
}
input {
  width: 400px;
  height: 30px;
}
button {
  background-color: green;
  color: #fff;
  font-weight: bold;
  border-radius: 50%;
  border: aqua 1px solid;
}
</style>
