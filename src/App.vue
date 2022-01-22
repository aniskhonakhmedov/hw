<template>
  <div id="app">
    <h1>Todo List</h1>
    <AddForm @ShareMyScreams="ParentFunction" />
    <hr />
    <main>
      <TodoItem
        v-for="item of todos"
        :key="item.key"
        :parent_info="item"
        v-on:delete_todo="remove_todo"
      />
    </main>
  </div>
</template>

<script>
import AddForm from "./components/AddForm.vue";
import TodoItem from "./components/TodoItem.vue";
export default {
  data() {
    return {
      todos: [
        {
          time: "18:44",
          title: "Купить молоко",
          isDeleted: false,
        },
      ],
    };
  },
  methods: {
    ParentFunction: function (text) {
      this.todos.push({
        id: this.todos.forEach((item, i) => item.id = i),
        time: new Date().getHours() + ":" + new Date().getSeconds(),
        title: text,
        isDeleted: false,
      });
    },
    remove_todo(id) {
      this.todos = this.todos.filter((item) => item.id !== id);
    },
  },
  components: {
    AddForm,
    TodoItem,
  },
};
</script>

<style>
* {
  font-family: "Gilroy";
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  width: 1000px;
  margin: 70px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  margin-bottom: 22px;
  font-size: 48px;
}

main {
  width: 100%;
  border-top: 1px solid rgba(0, 0, 0, 0.25);
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-auto-rows: 90px;
  grid-gap: 30px;
  padding-top: 20px;
  margin-top: 20px;
}
#TodoItem .aboutToDo {
  border-radius: 10px;
  border: 1px solid #007fff;
  background: #f0f0f0;
  display: flex;
  justify-content: space-between;
  padding: 25px 20px;
  align-items: start;
}

input[type="text"] {
  font-size: 16px;
  font-weight: 600;
  padding-left: 15px;
}

h5 {
  font-weight: 600;
  font-size: 18px;
}
i {
  font-weight: 500;
  font-size: 14px;
}
</style>