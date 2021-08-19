<template>
  <div class="todo-list">
    <TodoItem
      v-for="item in filterTodos"
      :key="item.id"
      :item="item"
      @changeState="$emit('changeState', item.id)"
      @removeTodo="$emit('removeTodo', item)"
      :class="{ completed: item.state == true }"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue"

export default {
  props: ["filterTodos"],
  name: "TodoList",
  components: {
    TodoItem,
  },

  methods: {},
}
</script>

<style scoped>
.todo-list {
  margin: 0 1.2rem;
}
</style>
