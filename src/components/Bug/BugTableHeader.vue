<template>
    <div class="bug-table-item bug-table-item--header">
        <div class="bug-table-item__cell" 
        v-for="header in getHeaders"
         :key="header.title">{{header.title}}</div>

    </div>
</template>
<script>
    export default {
        props : {
            headers_list : Array,
            columns_sort  : Array,
        },
        computed : {
            getHeaders () {
                return this.headers_list.sort((header1, header2) => this.columns_sort.indexOf(header1) - this.columns_sort.indexOf(header2))
            }
        }
    }
</script>