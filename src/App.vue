<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Calculadora></Calculadora>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Calculadora from './components/Calculadora.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Calculadora
  }
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
}
</style>
