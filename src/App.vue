<template>
  <div id="app">
    <toDoInput v-model="todoText" @keydown.enter="add"></toDoInput>
    <toDoListItem
      v-for="(item, index) in todolistArray"
      :key="index"
      :todo="item"
      @remove="removeTodo"
    >
    </toDoListItem>
  </div>
</template>

<script>
import toDoListItem from "@/components/toDoListItem";
import toDoInput from "@/components/toDoInput";

export default {
  name: "App",
  components: {
    // HelloWorld
    toDoListItem,
    toDoInput,
  },
  data() {
    return {
      todoText: "",
      todolistArray: [
        {
          id: 0,
          text: "什么事1",
        },
        {
          id: 1,
          text: "什么事2",
        },
      ],
    };
  },
  methods: {
    add() {
      this.todolistArray.push({
        id: this.todolistArray.length,
        text: this.todoText,
      });
      this.todoText = "";
    },
    removeTodo(id) {
      this.todolistArray = this.todolistArray.filter((item) => {
        return item.id != id;
      });
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
