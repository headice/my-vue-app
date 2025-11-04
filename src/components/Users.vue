<script setup>
import { ref, onMounted } from 'vue'

const users = ref([])
const loading = ref(true)

onMounted(async () => {
  try {
    const res = await fetch('https://dummyjson.com/users?limit=3')
    users.value = (await res.json()).users
  } finally {
    loading.value = false
  }
})
</script>

<template>
  <section>
    <h2>Users</h2>
    <p v-if="loading">Загрузка…</p>
    <ul v-else>
      <li v-for="u in users" :key="u.id">{{ u.firstName }} {{ u.lastName }}</li>
    </ul>
  </section>
</template>
