<script setup>
import { ref, watch, watchEffect } from 'vue'

const goal = ref(Math.floor(Math.random() * 100))
const count = ref('')
const message = ref(0)

// 限制count輸入數字範圍, 0-100
watchEffect(() => {
  if (count.value < 0) {
    count.value = 0
  } else if (count.value > 100) {
    count.value = 100
  }
})

// 監聽答案
watchEffect(() => {
  if (count.value === goal.value) {
    message.value = 'Correct !!'
  } else if (count.value > goal.value) {
    message.value = 'Too High !!'
  } else if (count.value < goal.value) {
    message.value = 'Too Low !!'
  }
})
</script>

<template>
  <div>
    <input v-model="count" type="number" />
    <p>Count: {{ count }}</p>
    <p>Message: {{ message }}</p>
  </div>

  <!-- {{ goal }} -->
</template>

<style scoped></style>
