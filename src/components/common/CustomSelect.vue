<template>
    <div class="custom-select" :class="{'custom-select--active': is_show}" ref="custom_select" @click.self.stop="showSelect">
        <div class="custom-select__value"></div>
        <div class="custom-select__inner">
            <div class="custom-select__option" :key="option.title+'_'+option.value" v-for="option in items">{{option.label}}</div>
        </div>
    </div>
</template>
<script>
export default {
    name : 'CustomSelect',
    data : {
        is_show : false,
    },
    props : {
        items : Array,
    },
    methods : {
        closeSelect (e) {
            const path = e.path || (e.composedPath && e.composedPath());
            if (e.target === this.$refs.custom_select || (path && path.indexOf(this.$refs.custom_select) > -1)) {

            } else {
                this.is_show = false;
            }

        },
        showSelect () {
            this.is_show = true;
        }
    },
    created () {
        document.addEventListener("click", this.closeSelect.bind(this));
    }
}
</script>

