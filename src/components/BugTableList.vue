<template>
<div class="bug-list">
    <h3 class="bug-list__header">Список багов</h3>
    <div class="bug-table">
        <BugTableHeader :headers_list="headers_list" :columns_sort="columns_sort"/>
        <TableItem v-for="bug, bug_index in bugs"
         :bug="bug"
          :key="bug_index"
          :bug_index="bug_index"
           :columns_sort="columns_sort"
           @changeBug="changeBug"/>

    </div> 
</div>

</template>
<script>
    import BugTableHeader from './Bug/BugTableHeader';
    import TableItem from './Bug/TableItem';

    export default {
        data () {
            return {
                columns_sort: ['description', 'priority', 'file', 'date_created', 'date_edited', 'author', 'assignee', 'status', 'comment', 'actions'],
                headers_list: [
                    {title: 'Описание', id: 'description'},
                    {title: 'Приоритет', id: 'priority'},
                    {title: 'Ссылка', id: 'file'},
                    {title: 'Создан', id: 'date_created'},
                    {title: 'Изменен', id: 'date_edited'},
                    {title: 'Автор', id: 'author'},
                    {title: 'Исполнитель', id: 'assignee'},
                    {title: 'Статус', id: 'status'},
                    {title: 'Коммент', id: 'comment'},
                    {title: 'Действия', id: 'actions'},
                    ],
                bugs : [
                    {
                        description: 'Какое-то описание, теоретически оно может быть довольно длинным',
                        priority: 1,
                        file: '',
                        date_created: +new Date() - 100000,
                        date_edited: +new Date() - 10000,
                        author: 'Портянко Н.',
                        assignee: 'Володин В.',
                        status: 'New',
                        comment: 'Не хочу фиксить',
                    },
                     {
                        description: 'Какое-то короткое описание',
                        priority: 20,
                        file: '',
                        date_created: +new Date() - 100000,
                        date_edited: +new Date() - 10000,
                        author: 'Кто-то тут Н.',
                        assignee: 'Кто-то там В.',
                        status: 'Need Check',
                        comment: 'Не хочу фиксить',
                    }
                ],

            }
        },
        methods : {
            changeBug (params) {
                let bug =  this.bugs[params.index];
                bug[params.id] = params.value;


            }
        },
        components : {
            BugTableHeader,
            TableItem
        }
    }
</script>

