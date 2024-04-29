<template>
  <div class="todo-app">
    <h1>"Daftar Kegiatan Anda"</h1>
    <p>create by Muhammad Rizki Ramadhani</p>

    <div class="filter-buttons">
      <button @click="filter = 'all'">Semua</button>
      <button @click="filter = 'done'">Selesai</button>
      <button @click="filter = 'pending'">Belum Selesai</button>
    </div>

    <input type="text" v-model="newTodo" placeholder="Masukkan item kegiatan baru" />
    <button @click="addTodo">Tambah</button>
    <hr>
    <ul>
      <li v-for="(todo, index) in filteredTodos" :key="index" :class="{ done: todo.done }">
        <input type="checkbox" v-model="todo.done" />
        <span>{{ todo.text }}</span>
        <button @click="removeTodo(index)">Hapus</button>
        <hr>
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
      filter: 'all', 
    };
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos;
      } else if (this.filter === 'done') {
        return this.todos.filter(todo => todo.done);
      } else if (this.filter === 'pending') {
        return this.todos.filter(todo => !todo.done);
      }
    },
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          text: this.newTodo,
          done: false,
        });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.todo-app {
  font-family: sans-serif;
  
}

ul > li > button{
  background-color: red;
  color: white;
}

.todo-app input[type="text"] {
  padding: 10px;
  margin-bottom: 10px;
}

.todo-app button {
  padding: 5px 10px;
  cursor: pointer;
}

.todo-app ul {
  list-style: none;
  padding: 0;
}

.todo-app li {
  margin-bottom: 10px;
}

.todo-app li input[type="checkbox"] {
  margin-right: 10px;
}

.todo-app li span {
  color: white;
  text-decoration: none;
}

.todo-app li button {
  float: right;
  padding: 5px;
  border: none;
  cursor: pointer;
}

.todo-app li.done span {
  text-decoration: line-through;
}

.filter-buttons {
  margin-bottom: 10px;
}

.filter-buttons button {
  padding: 5px 10px;
  margin-right: 5px;
  cursor: pointer;
  border: 1px solid #ccc;
}

.filter-buttons button.active {
  background-color: #eee;
}
</style>
