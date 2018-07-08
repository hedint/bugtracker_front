<template>
    <CustomSelect v-model="priority" :items="items" :empty_label="'Выберите приоритет'"/>
</template>
<script>
import CustomSelect from "../common/CustomSelect.vue";
export default {
  data() {
    return {
      priority: false,
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
  name: "ItemPriority",
  components: {
    CustomSelect
  }
};
</script>
