<template>
  <link
    rel="stylesheet"
    href="https://use.fontawesome.com/releases/v5.15.4/css/all.css"
    integrity="sha384-DyZ88mC6Up2uqS4h/KRgHuoeGwBcD4Ng9SiP4dIRy0EXTlnuz47vAwmeGwVChigm"
    crossorigin="anonymous"
  />
  <main>
    <div class="container">
      <AddTodo @createTodo="createTodo" />
      <Filters :selectedLabel="filterLabel" @changeFilter="changeFilter" />
      <TodoList
        :filterTodos="filterTodos"
        @changeState="changeState"
        @removeTodo="removeTodo"
      />
    </div>
  </main>
</template>

<script>
import AddTodo from "./components/AddTodo.vue"
import Filters from "./components/Filters.vue"
import TodoList from "./components/TodoList.vue"

export default {
  name: "App",
  components: {
    // HelloWorld
    AddTodo,
    Filters,
    TodoList,
  },
  data() {
    return {
      todoItems: [
        { id: 0, content: "have dinner", state: true },
        { id: 1, content: "test new project", state: false },
      ],
      filterTodos: [],
      filterLabel: "All",
    }
  },

  computed: {},

  methods: {
    check() {},
    updateFilterTodos() {
      this.filterTodos = []
      switch (this.filterLabel) {
        case "All": {
          this.filterTodos = this.todoItems
          break
        }
        case "Left": {
          this.todoItems.forEach((item) => {
            if (item.state == false) {
              this.filterTodos.push(item)
            }
          })
          break
        }
        case "Completed": {
          this.todoItems.forEach((item) => {
            if (item.state == true) {
              this.filterTodos.push(item)
            }
          })
          break
        }
      }
    },
    createTodo(inputContent) {
      this.todoItems.push({
        id: this.todoItems[this.todoItems.length - 1].id + 1,
        content: inputContent,
        state: false,
      })
      this.updateFilterTodos()
    },

    changeState(id) {
      this.todoItems.forEach((item) => {
        if (item.id === id) {
          item.state = !item.state
        }
      })
      // this.todoItems[id].state = !this.todoItems[id].state
      // alert(this.todoItems[id].state)
      this.updateFilterTodos(this.filterLabel)
      console.log(id + "selected")
    },
    changeFilter(label) {
      this.filterLabel = label
      this.updateFilterTodos()
    },
    removeTodo(item) {
      // alert(id)
      const index = this.todoItems.indexOf(item)
      this.todoItems.splice(index, 1)
      this.updateFilterTodos()
    },
  },

  created() {
    this.filterTodos = this.todoItems
  },
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300&family=Roboto:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: "Poppins", sans-serif;
}

main {
  width: 100vw;
  min-height: 100vh;
  background-color: #dee2ff;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  width: 60%;
  max-width: 480px;

  padding: 2rem 1rem;
  background-color: #fcfcfc;
  border-radius: 1rem;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

.container h1 {
  text-align: center;
  margin-bottom: 2rem;
  color: #414873;
}
</style>
