<template>
  <q-list bordered padding class="todo-list">
    <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" :index="index" @remove="removeTodo(index)" @toggle="animateToggle" />
  </q-list>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  props: {
    todos: Array,
  },
  components: {
    TodoItem,
  },
  methods: {
    removeTodo(index) {
      this.$emit('remove-todo', index);
    },
    animateToggle() {
      const notification = document.createElement('div');
      notification.className = 'notification toggled';
      notification.textContent = 'Item toggled';
      document.body.appendChild(notification);
      setTimeout(() => {
        document.body.removeChild(notification);
      }, 2000);
    }
  },
};
</script>

<style scoped>
.todo-list {
  padding: 0;
  background: #E8F5E9; /* Light Green */
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.notification {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: #388E3C; /* Dark Green */
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
  z-index: 1000;
  animation: fadeInOut 2s;
}

.notification.toggled {
  background: #34A853; /* Green */
}

@keyframes fadeInOut {
  0%, 100% { opacity: 0; }
  50% { opacity: 1; }
}
</style>
