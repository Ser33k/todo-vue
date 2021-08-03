<template>
  <div class="container">
    <div class="add-item">
      <input v-model="title" type="text" placeholder="To do...">
      <input v-model="date" type="date">
    </div>
    <div>
      <button @click="add">Add todo</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      date: "",
    };
  },
  methods: {
    add() {
      this.$emit("addItem", this.title, this.date);
      this.title = "";
      this.date = "";
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-around;
  width: 100%;
  margin: 40px 0;
}

input {
  font-size: 14px;
  margin: 5px;
  padding: 5px;
  width: 43%;
  height: 45%;
}

button {
  padding: 10px 20px;
  border: 1px solid black;
  background-color: black;
  color: white;
  border-radius: 4px;
  font-family: serif;
  text-transform: uppercase;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  color: black;
  background-color: white;
}
</style>

