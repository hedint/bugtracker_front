<template>
  <div :class="getClass">
    <i class="fas fa-edit" title="редактировать"></i>
  </div>
</template>
<script>
export default {
  name: 'ItemValue',
  props: {
    id: String,
  },
  computed: {
    getClass() {
      return `bug-table-item__${this.id}`;
    },
  },
  inheritAttrs: false,
};
</script>
