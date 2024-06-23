<template>
  <q-list bordered class="post-list">
    <q-item v-for="post in posts" :key="post.id" class="post-item">
      <slot name="post-item" :post="post">
        <q-item-section>
          <q-item-label class="post-item-title">{{ post.title }}</q-item-label>
          <q-item-label class="post-item-body">{{ post.body }}</q-item-label>
        </q-item-section>
      </slot>
    </q-item>
  </q-list>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.post-list {
  padding: 0 16px;
}

.post-item {
  padding: 16px;
  transition: background-color 0.3s, transform 0.3s;
}

.post-item:hover {
  background-color: #e8f5e9; /* Light Green */
  transform: translateX(5px);
}

.post-item-title {
  font-size: 1.25rem;
  color: #388e3c; /* Dark Green */
  font-weight: 500;
}

.post-item-body {
  font-size: 1rem;
  color: #666;
  margin-top: 8px;
}
</style>
