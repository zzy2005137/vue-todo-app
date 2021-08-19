<template>
  <div class="todo-item">
    <!-- <input type="checkbox" id="{{item.id}}" />
    <label for="{{item.id}}" class="todo-content"
      >{{ item.id }}{{ item.content }}</label
    >
    <button class="rm-btn">X</button> -->

    <label class="todo-content" :class="{ completed: item.state }">
      <input type="checkbox" @click="$emit('changeState')" />
      <span class="check-btn"></span>
      {{ item.content }}
      <button class="rm-btn" @click="$emit('removeTodo')">X</button>
    </label>
  </div>
</template>

<script>
export default {
  props: ["item"],
  name: "TodoItem",
}
</script>

<style scoped>
/* custom checkbox */

.todo-item {
  background-color: white;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  margin-bottom: 1rem;
  font-size: 1.2rem;
  border-radius: 0.5rem;
  padding: 0.5em;
  position: relative;
  display: flex;
  align-items: center;
}
/* hide the input */

.todo-item input[type="checkbox"] {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.todo-content {
  display: flex;
  /* align-items: center; */
  cursor: pointer;
}

/* .todo-content::before {
  content: "";
  border: 2px solid #2196f3;
  width: 1rem;
  height: 1rem;
  margin-right: 0.8rem;
  border-radius: 50%;
  top: 50%;
  transform: translate(0, 15%);
} */
.check-btn {
  display: flex;
}

.check-btn::after {
  content: "";
  border: 2px solid #2196f3;
  width: 1rem;
  height: 1rem;
  margin-right: 0.8rem;
  border-radius: 50%;
  top: 50%;
  transform: translate(0, 15%);
}

/* .todo-content:hover::before {
  background-color: #bde0fe;
} */

.todo-content:hover span::after {
  background-color: #bde0fe;
}

/* input[type="checkbox"]:checked ~ .check-btn::after, */
.todo-content.completed input[type="checkbox"] ~ .check-btn::after {
  content: "\002714";
  background-color: #bde0fe;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  border: 2px solid #bde0fe;
  transition: background-color 0.1s ease;
  font-size: 0.8em;
}

.rm-btn {
  width: 1.5em;
  height: 1.5em;
  background-color: #c81d25;
  border-radius: 50%;
  border: none;
  color: white;
  position: absolute;
  top: 50%;
  right: 1em;
  transform: translate(0, -50%);
  cursor: pointer;
  opacity: 0;
  transition: opacity 0.2s ease;
  font-size: 0.9rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.todo-item:hover .rm-btn {
  opacity: 1;
}
</style>
