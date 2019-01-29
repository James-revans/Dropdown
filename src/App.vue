<template>
  <div id="app">
    <Dropdown
    />
  </div>
</template>

<script>
import Dropdown from './components/Dropdown';


export default {
  name: 'app',
  components: {
    Dropdown

  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
