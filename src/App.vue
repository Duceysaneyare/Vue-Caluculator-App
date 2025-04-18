<template>
<div id="app">
  <calculator-app></calculator-app>

</div>
</template>

<script>
import CalculatorApp from './components/CalculatorApp.vue'

export default {
  name: 'App',
  components: {
    CalculatorApp
  }
}
</script>

<style>
body{
  background: #31475e !important;
}
</style>
