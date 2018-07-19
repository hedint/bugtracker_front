<template>
  <div :class="getClass">{{getText}}</div>
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
    getText() {
      const date = new Date();
      const cur_date = new Date();
      const val = this.date_created || this.date_edited;
      date.setTime(val);
      if (
        date.getFullYear() === cur_date.getFullYear() &&
        date.getDate() === cur_date.getDate() &&
        date.getMonth() === cur_date.getMonth()
      ) {
        return "Сегодня, " + this.getTime;
      }
      cur_date.setDate(cur_date.getDate() - 1);
      if (
        date.getFullYear() === cur_date.getFullYear() &&
        date.getDate() === cur_date.getDate() &&
        date.getMonth() === cur_date.getMonth()
      ) {
        return "Вчера, " + this.getTime;
      }
      return this.getDateTime();
    },
    getTime() {
      const date = new Date();
      const val = this.date_created || this.date_edited;
      date.setTime(val);
      return date.getHours() + ':' + date.getMinutes();
    },
    getDate () {
const date = new Date();
      const val = this.date_created || this.date_edited;
      date.setTime(val);
      return this.getDate() + '.' +(this.getMonth() + 1)
    },
    getDateTime () {
      return this.getDate() + ' ' + this.getTime();
    }
  }
};
</script>
