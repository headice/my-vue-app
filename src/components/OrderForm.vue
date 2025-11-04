<script setup>
import { reactive, computed, watch } from 'vue'

const form = reactive({ price: 1000, qty: 1, discount: 0 })
const total = computed(() => form.price * form.qty * (1 - form.discount / 100))

watch(() => form.qty, v => { if (v < 1) form.qty = 1 })
</script>

<template>
  <section>
    <h2>Order</h2>
    <input type="number" v-model.number="form.price" placeholder="Цена" />
    <input type="number" v-model.number="form.qty" placeholder="Кол-во" />
    <input type="number" v-model.number="form.discount" placeholder="Скидка %" />
    <p>Итого: {{ total }}</p>
  </section>
</template>
