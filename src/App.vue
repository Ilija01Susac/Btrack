<template>
  <Bus msg="Busevi"/>
  <Map msg="Ovo je mapa"/>
</template>

<script>
import Bus from './components/Bus.vue'
import Map from './components/map.vue'

export default {
  name: 'App',
  components: {
    Bus,
    Map
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
