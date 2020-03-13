<template>
  <div id="app">
    <h2>Composition API demo</h2>

    <button class="mr-1" @click="showCompositionApi">Composition Api</button>
    <button @click="showOptionApi">Option Api</button>

    <component :is="currentComponent" />
  </div>
</template>

<script>
import OptionApiDemo from './components/optionApiDemo.vue'
import CompositionApiDemo from './components/compositionApiDemo.vue'

export default {
  name: 'App',
  components: {
    CompositionApiDemo,
    OptionApiDemo,
  },
  data () {
    return {
      currentComponent: OptionApiDemo.name,
    }
  },
  methods: {
    showCompositionApi () {
      this.currentComponent = CompositionApiDemo.name
    },
    showOptionApi () {
      this.currentComponent = OptionApiDemo.name
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 1.4em;
}

button {
  box-shadow: 0px 1px 0px 0px #fff6af;
  background: linear-gradient(to bottom, #ffec64 5%, #ffab23 100%);
  background-color: #ffec64;
  border-radius: 6px;
  border: 1px solid #ffaa22;
  display: inline-block;
  cursor: pointer;
  color: #333333;
  font-family: Arial;
  font-size: 15px;
  font-weight: bold;
  padding: 10px 24px;
  text-decoration: none;
  text-shadow: 0px 1px 0px #ffee66;
}
button:hover {
  background: linear-gradient(to bottom, #ffab23 5%, #ffec64 100%);
  background-color: #ffab23;
}
button:active {
  position: relative;
  top: 1px;
}

.mr-1 {
  margin-right: 15px;
}
</style>
