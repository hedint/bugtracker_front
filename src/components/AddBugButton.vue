<template>
  <div class="add-bug-button" title="Создать баг">
    <i class="fas fa-plus-circle fa-3x"></i>
  </div>
</template>
<script>
export default {
  name: "AddBugButton"
};
</script>
<style lang="stylus">
.add-bug-button 
  position fixed
  top 50px
  right 50px
  width 50px
  height 50px
  cursor pointer
  i
    width 100%
    height 100%
</style>