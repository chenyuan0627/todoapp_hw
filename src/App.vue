<template>
  <div>
    <h1 style="font-family: '微軟黑正體'; font-weight: bold; text-align: center;">★ 今天的待辦事項 ★</h1>
    <div style="text-align: center;">
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="新增待辦事項" style="font-size: 20px; padding: 5px; width: 40%; text-align: center;" />
      <button @click="addTodo" class="macaron-button" style="margin-left: 10px;">新增</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <div class="todo-item">
          <input type="checkbox" v-model="todo.completed" class="checkbox" style="transform: scale(1.5); margin-left: -30px;" />
          <div class="todo-content">
            <span :class="{ completed: todo.completed }" class="todo-text">{{ todo.text }}</span>
            <button @click="removeTodo(index)" class="macaron-button">刪除</button>
          </div>
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
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === '') return;
      this.todos.push({ text: this.newTodo, completed: false });
      this.newTodo = '';
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}

.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #ccc;
  padding: 8px;
}

.checkbox {
  margin-right: 20px;
}

.todo-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.todo-text {
  font-size: 20px;
  font-family: '微軟黑正體';
  font-weight: bold;
}

.macaron-button {
  background-color: #95e0c3;
  color: black;
  border: none;
  cursor: pointer;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 16px;
  font-weight: bold;
}

.macaron-button:hover {
  color: white;
  font-weight: bold;
  background-color: #3e6353d8;
}
</style>
