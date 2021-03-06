<template>
  <div id="app">
    <h1>ToDo Vue</h1>
    <input type="text" v-model="newToDo" v-on:keyup.enter="add" />
    <button v-on:click="add()">Add</button>
    <ul>
      <li style="list-style-type: none" v-for="(todo, i) in existingToDo">
        {{ i + 1 }}: {{ todo.text }}
        <button v-on:click="deleteToDo(i)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newToDo: "",
      existingToDo: [
        { text: "Shopping", id: 1 },
        { text: "Projects", id: 2 }
      ]
    };
  },
  methods: {
    add() {
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
        (this.newToDo = "");
    },
    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    }
  }
};
</script>

<style></style>
