<template>
  <q-item clickable :class="{ 'q-item--active': todo.done }" class="todo-item q-pa-sm">
    <q-item-section avatar>
      <q-checkbox v-model="todo.done" color="primary" @update:model-value="$emit('toggle')" />
    </q-item-section>
    <q-item-section>
      <q-item-label>{{ todo.text }}</q-item-label>
    </q-item-section>
    <q-item-section side>
      <q-btn @click="$emit('remove', index)" color="negative" icon="cancel" flat />
    </q-item-section>
  </q-item>
</template>

<script>
export default {
  props: {
    todo: Object,
    index: Number,
  },
  emits: ['remove', 'toggle'],
};
</script>

<style scoped>
.todo-item {
  background: #e8f5e9; /* Light Green */
  color: black;
  border-radius: 8px;
  margin-bottom: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.todo-item:hover {
  background: #c8e6c9; /* Slightly darker light green */
}

.q-item--active .q-item__label {
  text-decoration: line-through;
  color: #388e3c; /* Dark Green */
}

.q-checkbox input:checked ~ .q-checkbox__bg {
  background-color: #34A853; /* Checkbox Green */
  border-color: #34A853;
}

.q-btn[color="negative"] {
  color: white;
  background-color: #e57373; /* Light Red */
}
</style>
