<template>
  <div class="root">
    <h1>TodoApp</h1>
    <AddItem @addItem="addToDo" />
    <ul class="list">
      <ToDoItem @deleteClick="deleteItem" @doneClick="toDoDone" v-for="item in list" :key="item.id" :item="item" />
    </ul>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue";
import AddItem from "./AddItem.vue";

export default {
  name: "ToDoApp",
  components: {
    ToDoItem,
    AddItem,
  },
  data() {
    return {
      list: [
        { title: "Zrobić zakupy", date: "2021-05-12", done: false, id: 22 },
      ],
    };
  },
  methods: {
    toDoDone(id) {
      const index = this.list.findIndex((item) => item.id === id);
      this.list[index].done = true;
    },
    addToDo(title, date) {
      this.list.push({ title, date, done: false, id: Math.random() * 20 });
    },
    deleteItem(id) {
      this.list = this.list.filter((el) => el.id !== id);
    },
  },
};
</script>

<style scoped>
.list {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>