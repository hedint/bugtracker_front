<template>
  <div :class="getClass">{{value}}</div>
</template>
<script>
export default {
  name: "ItemValue",
  props : {
    id : String,
  },
  computed: {
    getClass() {
      return `bug-table-item__${this.id}`;
    }
  },
  inheritAttrs: false
};
</script>
