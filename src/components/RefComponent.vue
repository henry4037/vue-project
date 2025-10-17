<script setup>
import { ref, onMounted } from 'vue'

const inputData = ref([])
const items = ref([
  { id: 1, name: '蘋果', placeholder: '請輸入數量' },
  { id: 2, name: '橘子', placeholder: '請輸入數量' },
  { id: 3, name: '香蕉', placeholder: '請輸入數量' },
])

//???
const setInputRef = (index, element) => {
  inputData.value[index] = element
}

//送出資料
const submit = () => {
  inputData.value.forEach((input, index) => {
    console.log('🚀 ~ submit ~ input:', input)
    console.log(`${items.value[index].name} 數量 ${input.value}`)
  })
}

//清空所有輸入欄位 + 聚焦第一欄位
const focusFirstInput = () => {
  inputData.value.forEach((input) => {
    input.value = ''
  })

  if (inputData.value[0]) {
    inputData.value[0].focus()
  }
}

//聚焦第一欄位
onMounted(() => {
  if (inputData.value[0]) {
    inputData.value[0].focus()
  }
})
</script>

<template>
  <div>
    <div v-for="(item, index) in items" :key="item.id">
      <label> {{ item.name }}</label>
      <input type="text" :ref="(el) => setInputRef(index, el)" :placeholder="item.placeholder" />
    </div>
    <button @click="focusFirstInput">重新輸入(聚焦第一個輸入框)</button>
    <button @click="submit">送出</button>
  </div>
</template>

<style scoped>
input {
  margin: 5px;
}
</style>
