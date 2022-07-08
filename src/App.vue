<template>
  <Pricing/>
</template>

<script>
import Pricing from './views/Pricing.vue'

export default {
  name: 'App',
  components: {
    Pricing
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Montserrat', sans-serif;
  font-size: 1em;
  background: $very-light-grayish-blue;
  color: $grayish-blue;
  max-width: 1400px;
  margin: 0 auto;
}
</style>