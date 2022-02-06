<script setup lang="js">
import CarECommerce from './components/CarECommerce.vue'

export default {
  name: 'App',
  components: {
    CarECommerce
  }
}
</script>

<template>
  <CarECommerce></CarECommerce>
</template>


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
