<template>
  <div id="app">
    <ItemPriority/>
  </div>
</template>

<script>
import ItemPriority from './components/Bug/ItemPriority.vue';

export default {
  name: 'app',
  components: {
    ItemPriority,
  },
};
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>
