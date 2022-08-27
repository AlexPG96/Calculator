<template>
  <div id="app">
    <h3>Calculator with Vue JS</h3>
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>
<style>
body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>