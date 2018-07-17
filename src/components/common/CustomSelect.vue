<template>
    <div class="custom-select" :class="{'custom-select--active': is_show}" ref="custom_select" @click.stop="showSelect">
        <div class="custom-select__value">{{getTitle}}</div>
        <div class="custom-select__inner">
            <div class="custom-select__option" :style="getStyle" :key="option.title+'_'+option.value" v-for="option in items" @click.stop="optionPick(option)">
                <div class="custom-select__label">{{option.label}}</div>
                <div class="custom-select__icon" v-if="option.icon">
                    <img :src="option.icon" />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  name: "CustomSelect",
  data() {
    return { is_show: false };
  },
  props: {
    items: Array,
    empty_label: String,
    value: [String, Number, Boolean]
  },
  computed: {
    getActiveOption() {
      return this.items.find(option => option.value === this.value);
    },
    getTitle() {
      return this.getActiveOption
        ? this.getActiveOption.label
        : this.empty_label;
    },
    getStyle() {
      return this.getActiveOption && this.getActiveOption.color
        ? this.getActiveOption.color
        : false;
    }
  },
  methods: {
    closeSelect(e) {
      const path = e.path || (e.composedPath && e.composedPath());
      if (
        e.target === this.$refs.custom_select ||
        (path && path.indexOf(this.$refs.custom_select) > -1)
      ) {
      } else {
        this.is_show = false;
      }
    },
    optionPick(option) {
      this.$emit("input", option.value);
      this.is_show = false;
    },
    showSelect() {
      this.is_show = true;
    }
  },
  created() {
    document.addEventListener("click", this.closeSelect.bind(this));
  },
  updated() {}
};
</script>
<style lang="stylus">
.custom-select {
    cursor: pointer;
    position: relative;

    &--active {
        .custom-select__inner {
            display: block;
        }
    }

    &__inner {
        display: none;
        position: absolute;
        z-index: 10;
        background: white;
        width: 100%;
    }
}
</style>