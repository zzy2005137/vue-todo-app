<template>
  <h1>What's Up Friend</h1>

  <div class="todo-input">
    <label for="input-content"></label>
    <input
      type="text"
      id="input-content"
      autocomplete="off"
      v-model="inputContent"
      @keyup.enter="check"
    />
    <button @click="check">
      <i class="fas fa-plus"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      inputContent: "",
    }
  },
  methods: {
    check() {
      if (this.inputContent !== "") {
        this.$emit("createTodo", this.inputContent)
        this.inputContent = ""
      }
    },
  },
}
</script>

<style scoped>
.todo-input {
  margin: 1rem;
  position: relative;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  border-radius: 1rem;
}

.todo-input input {
  width: 100%;
  padding: 0.6rem 1rem;
  border: none;
  outline: none;
  border-radius: 1rem;
}

.todo-input button {
  position: absolute;
  top: 50%;
  transform: translate(0, -50%);
  right: 0rem;
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  background-color: #3d5a80;

  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
}
</style>
