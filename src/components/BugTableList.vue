<template>
    <div class="bug-list">
        <h3 class="bug-list__header">Список багов</h3>
        <div class="bug-table">
            <BugTableHeader :headers_list="headers_list" :columns_sort="columns_sort" />
            <TableItem v-for="(bug, bug_index) in bugs"
             :bug="bug" 
             :key="bug_index"
             :bug_index="bug_index"
             :columns_sort="columns_sort"
              @changeBug="changeBug" />

        </div>
    </div>

</template>
<script>
import BugTableHeader from "./Bug/BugTableHeader";
import TableItem from "./Bug/TableItem";

export default {
  data() {
    return {
      columns_sort: [
        "description",
        "priority",
        "images",
        "date_created",
        "date_edited",
        "author",
        "assignee",
        "status",
        "comment",
        "actions"
      ],
      headers_list: [
        { title: "Описание", id: "description" },
        { title: "Приоритет", id: "priority" },
        { title: "Ссылка", id: "images" },
        { title: "Создан", id: "date_created" },
        { title: "Изменен", id: "date_edited" },
        { title: "Автор", id: "author" },
        { title: "Исполнитель", id: "assignee" },
        { title: "Статус", id: "status" },
        { title: "Коммент", id: "comment" },
        { title: "Действия", id: "actions" }
      ],
      bugs: [
        {
          description:
            "Какое-то описание, теоретически оно может быть довольно длинным",
          priority: 1,
          images: "https://www.gettyimages.ie/gi-resources/images/Homepage/Hero/UK/CMS_Creative_164657191_Kingfisher.jpg",
          date_created: +new Date() - 86400000,
          date_edited: +new Date() - 10000,
          author: "Портянко Н.",
          assignee: "Володин В.",
          status: 1,
          comment: "Не хочу фиксить"
        },
        {
          description: "Какое-то короткое описание",
          priority: 20,
          images: [
            'https://cdn.pixabay.com/photo/2017/01/06/23/21/soap-bubble-1959327_960_720.jpg',
            'https://i.pinimg.com/originals/94/dd/57/94dd573e4b4de604ea7f33548da99fd6.jpg'
          ],
          date_created: +new Date() - 86400000,
          date_edited: +new Date() - 10000,
          author: "Кто-то тут Н.",
          assignee: "Кто-то там В.",
          status: 3,
          comment: "Не хочу фиксить"
        },
      ]
    };
  },
  methods: {
    changeBug(params) {
      let bug = this.bugs[params.index];
      bug[params.id] = params.value;
    }
  },
  components: {
    BugTableHeader,
    TableItem,
  },
};
</script>

