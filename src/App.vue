<template>
  <div id="app">
    <Elevator> </Elevator>
  </div>
</template>

<script>
import Elevator from './components/Elevator.vue'

export default {
  name: 'App',
  components: {
    Elevator
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
