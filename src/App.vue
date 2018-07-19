<template>
  <div id="app">
    <BugTableList/>
    <AddBugButton/>
  </div>
</template>

<script>
import BugTableList from "./components/BugTableList.vue";
import AddBugButton from "./components/AddBugButton.vue";

import styl from "./styles/main.styl";
export default {
  name: "app",
  components: {
    BugTableList,
    AddBugButton
  }
};
</script>

<style lang="stylus">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
