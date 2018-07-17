<template>
  <div :class="getClass">{{getValue}}</div>
</template>
<script>
export default {
  name: "ItemDate",
  props: {
    id: String,
    date_created: {
      type: Number,
      required: false
    },
    date_edited: {
      type: Number,
      required: false
    }
  },
  computed: {
    getClass() {
      return `bug-table-item__${this.id}`;
    },
    getValue() {
      const date = new Date();
      const val = this.date_created || this.date_edited;
      date.setTime(val);
      return date.toLocaleString();
    }
  }
};
</script>
