<script setup>
import { ref, computed } from 'vue'

const count = ref(0)
const doubled = computed(() => count.value * 2)
</script>

<template>
  <section>
    <h2>Counter</h2>
    <p>{{ count }} / x2: {{ doubled }}</p>
    <button @click="count++">+</button>
  </section>
</template>
