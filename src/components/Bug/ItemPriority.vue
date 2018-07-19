<template>
  <div class="bug-table-item__priority">
    <CustomSelect :value="priority" @input="changeValue" :items="items" :empty_label="'Приоритет:'" />
  </div>
</template>
<script>
import CustomSelect from "../common/CustomSelect.vue";
export default {
  name: "ItemPriority",
  data() {
    return {
      items: [
        {
          value: 1,
          label: "minor",
          color: "green"
        },
        {
          value: 10,
          label: "major",
          color: "#ff7514"
        },
        {
          value: 20,
          label: "critical",
          color: "#ff2400"
        },
        {
          value: 30,
          label: "blocker",
          color: "#c51d34"
        }
      ]
    };
  },
  props: {
    priority: Number,
    id: String
  },
  name: "ItemPriority",
  methods: {
    changeValue(value) {
      this.$emit("changeValue", { value, id: this.id });
    }
  },
  components: {
    CustomSelect
  },
  updated() {}
};
</script>
