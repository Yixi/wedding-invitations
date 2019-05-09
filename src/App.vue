<template>
  <div>
    <slider></slider>
    <Address></Address>
  </div>
</template>

<script>
  import Slider from './components/Slider.vue'
  import Address from './components/address'

  export default {
    name: 'app',
    components: {
      Slider,
      Address
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
