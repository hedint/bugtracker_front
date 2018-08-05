<template>
  <div class="bug-table-item">
    <div class="bug-table-item__cell" v-for="cell in getCells" :key="cell.id">
      <component :is="cell.component" v-bind="cell.value" @changeValue="changeBug" />
    </div>
  </div>
</template>
<script>
import ItemPriority from './ItemPriority.vue';
import ItemStatus from './ItemStatus.vue';
import ItemValue from './ItemValue.vue';
import ItemDate from './ItemDate.vue';
import ItemDescription from './ItemDescription.vue';
import ItemActions from './ItemActions.vue';
import ItemImage from './ItemImage.vue';




export default {
  data() {
    return {
      cells: [
        { id: 'images', component: ItemImage, value: false },
        { id: 'description', component: ItemDescription, value: false },
        { id: 'priority', component: ItemPriority, value: false },
        { id: 'date_created', component: ItemDate, value: false },
        { id: 'date_edited', component: ItemDate, value: false },
        { id: 'author', component: ItemValue, value: false },
        { id: 'assignee', component: ItemValue, value: false },
        { id: 'status', component: ItemStatus, value: false },
        { id: 'comment', component: ItemValue, value: false },
        { id: 'actions', component: ItemActions, value: false }
      ]
    };
  },
  props: {
    bug: Object,
    bug_index: Number,
    columns_sort: Array
  },
  computed: {
    getCells() {
      return this.cells
        .slice()
        .sort(
          (cell1, cell2) =>
            this.columns_sort.indexOf(cell1.id) -
            this.columns_sort.indexOf(cell2.id)
        )
        .map(cell => {
          return {
            ...cell,
            value: { [cell.id]: this.bug[cell.id], id: cell.id }
          };
        });
    }
  },
  components: {
    ItemPriority,
    ItemStatus,
    ItemValue,
    ItemDate,
    ItemDescription,
    ItemActions,
    ItemImage,
  },
  methods: {
    changeBug(params) {
      this.$emit("changeBug", { ...params, index: this.bug_index });
    }
  },
};
</script>

