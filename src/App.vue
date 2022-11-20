<template>
  
  <PokemonComponent></PokemonComponent>
</template>

<script>
import PokemonComponent from './components/PokemonComponent.vue'

export default {
  name: 'App',
  components: {
    PokemonComponent,
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
  /*margin-top: 60px;*/
}
</style>
