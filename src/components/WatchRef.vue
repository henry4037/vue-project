<script setup>
import { ref, watch } from 'vue'

const text = ref('')
const length = ref(0)
const isTooLong = ref(false)

watch(text, (newvalue, oldvalue) => {
  length.value = text.value.length

  if (length.value > 10) {
    isTooLong.value = true
  } else [(isTooLong.value = false)]
})
</script>

<template>
  <div class="container">
    <h2>輸入文字監聽示範（watch）</h2>
    <input v-model="text" placeholder="輸入任意文字..." />

    <p>目前輸入字串長度：{{ length }}</p>
    <p v-if="isTooLong" style="color: red">⚠️ 文字長度超過 10 字元！</p>
    <p v-else style="color: green">✅ 文字長度在範圍內</p>
  </div>
</template>

<style scoped>
.container {
  max-width: 400px;
  margin: 40px auto;
  font-family: Arial, sans-serif;
}
input {
  width: 100%;
  font-size: 16px;
  padding: 8px;
  margin-bottom: 12px;
  border: 1px solid #ccc;
  border-radius: 6px;
}
</style>
