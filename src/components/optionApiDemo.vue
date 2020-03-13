<template>
  <div id="app">
    <h3>Option API todo demo ({{ todos.length }})</h3>

    <div v-if="!loading">
      <div v-for="todo in todos" :key="todo.id">
        <strong>{{ todo.title }} </strong>
        ({{ todo.completed ? 'DONE!' : 'incomplete' }})
      </div>
    </div>

    <div v-else>
      <div style="color: #666;">Loading...</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'OptionApiDemo',
  components: {},
  data () {
    return {
      loading: false,
      todos: [],
    }
  },
  mounted () {
    this.loading = true
    axios
      .get('https://jsonplaceholder.typicode.com/todos')
      .then(r => r.data)
      .then(todos => {
        setTimeout(
          (td => {
            this.todos = td
            this.loading = false
          }).bind(this),
          1000, // Fake a long request
          todos
        )
      })
  },
  computed: {
    todoCount () {
      return this.todos.length
    },
  },
}
</script>

<style></style>
