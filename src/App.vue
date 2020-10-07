<template>
  <div id="app">
    <v-main-wrapper/>
  </div>
</template>

<script>
import vMainWrapper from './components/v-main-wrapper'

export default {
  name: 'App',
  components: {
    vMainWrapper,
  }
}
</script>

<style>
  #app{
    max-width: 1200px;
    margin: 0 auto;
  }
</style>