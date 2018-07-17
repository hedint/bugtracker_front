<template>
  <div :class="getClass" v-html="description"></div>
</template>
<script>
export default {
  props: {
    id: String,
    description: String
  },
  computed: {
    getClass() {
      return `bug-table-item__${this.id}`;
    }
  }
};
</script>
