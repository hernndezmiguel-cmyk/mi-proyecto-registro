<template>
  <div id="app">
    <FormularioRegistro />
  </div>
</template>

<script>
import FormularioRegistro from './components/FormularioRegistro.vue'

export default {
  name: 'App',
  components: {
    FormularioRegistro
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #f5f5f5;
  min-height: 100vh;
  padding: 20px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>