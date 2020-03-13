<template>
  <div id="app">
    <h3>Composition API todo demo ({{ todoCount }})</h3>

    <button @click="getMoreTodos">Load more...</button>

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
import { reactive, toRefs, computed } from '@vue/composition-api'

export default {
  name: 'CompositionApiDemo',
  components: {},
  setup () {
    const { loading, todos, todoCount, fetchMore } = getTodos()

    return { loading, todos, todoCount, getMoreTodos: fetchMore }
  },
}

// This could be extracted into it's own file
function getTodos () {
  const state = reactive({
    loading: false,
    todos: [],
  })

  const todoCount = computed(() => state.todos.length)

  // Added support for fetching more data
  function fetchMore () {
    state.loading = true
    axios
      .get('https://jsonplaceholder.typicode.com/todos')
      .then(r => r.data)
      .then(serverTodos => {
        setTimeout(
          td => {
            state.todos = state.todos.concat(td)
            state.loading = false
          },
          1000, // Fake long request time
          serverTodos
        )
      })
  }

  fetchMore()

  return { ...toRefs(state), todoCount, fetchMore }
}
</script>

<style></style>
