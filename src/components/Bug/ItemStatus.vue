<template>
    <div class="bug-table-item__status">
        <CustomSelect :value="status" @input="changeValue" :items="items" :empty_label="'Статус:'" />
    </div>
</template>
<script>
import CustomSelect from "../common/CustomSelect.vue";
export default {
  name: "ItemStatus",
  props: {
    status: Number,
    id: String
  },
  data() {
    return {
      items: [
        {
          value: 1,
          label: "New"
        },
        {
          value: 2,
          label: "Reopen"
        },
        {
          value: 3,
          label: "Need check"
        },
        {
          value: 4,
          label: "Fixed"
        }
      ]
    };
  },
  methods: {
    changeValue(value) {
      this.$emit("changeValue", { value, id: this.id });
    }
  },
  components: {
    CustomSelect
  }
};
</script>

