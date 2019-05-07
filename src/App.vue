<template>
  <div>
    <slider></slider>
  </div>
</template>

<script>
  import Slider from './components/Slider.vue'

  export default {
    name: 'app',
    components: {
      Slider
    }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    outline: 0;
  }

  body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
</style>
