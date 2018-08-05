<template>
    <div class="custom-select" 
    :class="{'custom-select--active': is_show}"
    ref="custom_select"
    @click.stop="showSelect">
        <div class="custom-select__value" :style="getStyle">{{getTitle}}
          <i class="fas fa-angle-down" v-if="!is_show"></i>
          <i class="fas fa-angle-up" v-if="is_show"></i>
        </div>
        <div class="custom-select__inner">
            <div class="custom-select__option"
            :style="getOptionStyle(option)"
            :key="option.title+'_'+option.value"
            v-for="option in items"
            @click.stop="optionPick(option)">
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
  name: 'CustomSelect',
  data() {
    return { is_show: false };
  },
  props: {
    items: Array,
    empty_label: String,
    value: [String, Number, Boolean],
  },
  computed: {
    getActiveOption() {
      return this.items.find(option => option.value === this.value);
    },
    getStyle() {
      let style = {};
      if (this.getActiveOption && this.getActiveOption.color) {
        style.color = this.getActiveOption.color;
      }
      return style;
    },
    getTitle() {
      return this.getActiveOption
        ? this.getActiveOption.label
        : this.empty_label;
    },
  },
  methods: {
    closeSelect(e) {
      const path = e.path || (e.composedPath && e.composedPath());
      if (
        e.target === this.$refs.custom_select ||
        (path && path.indexOf(this.$refs.custom_select) > -1)
      ) {
        //do nothing
      } else {
        this.is_show = false;
      }
    },
    getOptionStyle(option) {
      const style = {};
      if (option.color) {
        style.color = option.color;
      }
      return style;
    },
    optionPick(option) {
      this.$emit('input', option.value);
      this.is_show = false;
    },
    showSelect() {
      this.is_show = !this.is_show;
    },
  },
  created() {
    document.addEventListener('click', this.closeSelect.bind(this));
  },
};
</script>
<style lang="stylus">
.custom-select {
    cursor pointer
    position relative
    user-select none
    min-width 110px
    &--active {
        .custom-select__inner {
            display block
        }
    }
    &__value {
      //border 1px solid black
      padding 4px 16px 4px 4px
      position relative
      i {
        position absolute
        right 6px
        color black
        display none
      }
      &:hover {
        i {
          display inline-block
        }
      }
    }

    &__inner {
        display none
        position absolute
        z-index 10
        background white
        width 100%
        border 1px solid black
        padding 4px 16px 4px 4px

    }
}
</style>
