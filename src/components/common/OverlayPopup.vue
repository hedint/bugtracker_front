<template>
  <div class="overlay-popup" @click="overlayClick">
    <slot/>
  </div>
</template>
<script>
export default {
  name : 'OverlayPopup',
  methods : {
    overlayClick () {
      this.$emit('overlayClick');
    }
  },
};
</script>
<style lang="stylus">
  .overlay-popup
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    background rgba(0, 0, 0, 0.5)
    display flex
    justify-content center
    align-items center
    z-index 1000
  
</style>
