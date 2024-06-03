<template>
  <div class="todo-app">
    <h1>Todo List</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new item" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
        <div class="actions">
          <label class="custom-checkbox">
            <input type="checkbox" v-model="todo.done" />
            <span class="checkmark"></span>
          </label>
          <button @click="removeTodo(index)">x</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, done: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
*:focus, *:hover {
  outline: none;
}

.todo-app {
  width: 450px;
  max-width: 450px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  background-color:#9DB2BF;
  border-radius: 10px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}

h1 {
  margin-bottom: 20px;
  font-size: 34px;
  color: #27374D;
  font-family: 'Courier New', Courier, monospace;
}

input {
  width: 90%;
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  border-radius: 10px;
  outline: none;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  font-size: 20px;
  transition: all 0.3s ease;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

input[type="text"]:focus {
  border: none;
  outline: none;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 35px;
  word-wrap: break-word;
  border-top: 1px solid #ccc;
}

li .done {
  text-decoration: line-through;
}

li span {
  flex: 1;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 27px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.actions {
  width: 85px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.custom-checkbox {
  display: flex;
  align-items: center;
  justify-content: center;
}

.custom-checkbox input {
  opacity: 0;
  width: 0;
  height: 0;
}

.custom-checkbox .checkmark {
  width: 34px; /* Set width */
  height: 34px; /* Set height */
  background-color: #eee;
  border-radius: 50px;
  position: relative;
  cursor: pointer;
  transition: background-color 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.custom-checkbox .checkmark:after {
  content: "";
  position: absolute;
  display: none;
  left: 10px;
  top: 3px;
  width: 11px;
  height: 22px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.custom-checkbox input:checked + .checkmark {
  background-color: #20e977;
}

.custom-checkbox input:checked + .checkmark:after {
  display: block;
}

button {
  width: 34px;
  height: 34px;
  background: #ff4e4e;
  border: none;
  color: white;
  padding-bottom: 5px;
  border-radius: 50px;
  cursor: pointer;
  transition: background 0.3s ease;
  font-size: 24px;
}

button:hover {
  background: #ff0000;
}
</style>
