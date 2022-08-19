<template>
  <Calc msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Calc from './components/Calc/Calc.vue'

export default {
  name: 'App',
  components: {
    Calc
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
}

#app {
  display: flex;
  height: 100vh;
  width: 100vw;
  justify-content: center;
  align-items: center;
  background: linear-gradient(116.82deg, rgba(247, 183, 24, 0.7) 0%, rgba(245, 197, 78, 0.6) 100%);
}
</style>
