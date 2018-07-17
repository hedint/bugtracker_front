<template>
  <div :class="getClass">{{value}}</div>
</template>
<script>
export default {
  name: "ItemValue",
  data() {
    return {
      id: this.$attrs.id,
      value: this.$attrs[this.$attrs.id]
    };
  },
  computed: {
    getClass() {
      return `bug-table-item__${this.id}`;
    }
  },
  inheritAttrs: false
};
</script>
