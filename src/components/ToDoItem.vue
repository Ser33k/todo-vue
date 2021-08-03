<template>
  <li class="item" :class="{done: item.done}">
    <h2>{{ item.title }}</h2>
    <h6>{{ item.date }}</h6>
    <button v-if="!item.done" @click="done" :disabled="item.done" class="btn done-btn">DONE</button>
    <button v-else @click="deleteItem" class="btn delete">X</button>
  </li>
</template>

<script>
export default {
  name: "item",
  props: ["item"],
  methods: {
    done() {
      this.$emit("doneClick", this.item.id);
    },
    deleteItem() {
      this.$emit("deleteClick", this.item.id);
    },
  },
};
</script>

<style scoped>
.item {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  border-bottom: 1px solid black;
  margin-bottom: 10px;
  padding: 10px;
}

.done {
  opacity: 0.5;
}

.btn {
  padding: 10px;
  height: 50%;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}

.done-btn {
  background-color: rgb(61, 150, 76);
  border: none;
}

.done-btn:hover {
  background-color: rgb(43, 100, 52);
}

.delete {
  background-color: #db1818;
  border: none;
}

.delete:hover {
  background-color: #881515;
}
</style>