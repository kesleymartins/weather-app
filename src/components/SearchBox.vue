<script setup>
import { ref } from 'vue'

const query = ref('')
const emit = defineEmits(['search'])

const emitSearch = () => {
  emit('search', query.value)
}
</script>

<template>
  <div class="search-box">
    <input type="text" class="search-bar" placeholder="Search..." v-model="query" @keyup.enter="emitSearch" />
  </div>
</template>

<style scoped>
.search-box {
  display: flex;
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  background-color: rgba(255, 255, 255, 0.75);
}
</style>
