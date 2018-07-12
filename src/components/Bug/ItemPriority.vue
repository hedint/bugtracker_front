<template>
    <div class="bug-table-item__priority">
          <CustomSelect :value="priority" @input="changeValue" :items="items" :empty_label="'Выберите приоритет'"/>
    </div>
</template>
<script>
import CustomSelect from "../common/CustomSelect.vue";
export default {
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
          color: "red"
        },
        {
          value: 20,
          label: "critical",
          color: "red"
        },
        {
          value: 30,
          label: "blocker",
          color: "red"
        }
      ]
    };
  },
  props : {
    priority : Number,
    id : String,
  },
  name: "ItemPriority",
  methods : {
    changeValue (value) {
      this.$emit('changeValue', {value, id : this.id})
    }
  },
  components: {
    CustomSelect
  },
  updated () {
  }
};
</script>
