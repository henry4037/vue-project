<template>
  <div class="container">
    <h2>🛒 商品管理系統</h2>

    <!-- 商品輸入表單 -->
    <form @submit.prevent="handleSubmit">
      <input v-model="form.name" placeholder="商品名稱" required />
      <input v-model.number="form.price" type="number" placeholder="價格" required />

      <button type="submit">
        {{ form.id ? '更新商品' : '新增商品' }}
      </button>

      <button v-if="form.id" type="button" @click="resetForm">取消編輯</button>
    </form>

    <hr />

    <!-- 商品清單 -->
    <ProductItemComp
      v-for="product in products"
      :key="product.id"
      :product="product"
      @edit="editProduct"
      @delete="removeProduct"
    />

    <p v-if="products.length === 0">⚠️ 沒有商品</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProductItemComp from './ProductItemComp.vue'

//商品起始id = 1
let nextId = 1

//起始預設商品
const products = ref([
  { id: nextId++, name: '滑鼠', price: 500 },
  { id: nextId++, name: '鍵盤', price: 800 },
  { id: nextId++, name: '顯示器', price: 3000 },
])

//定義表單欄位
const form = ref({
  id: null,
  name: '',
  price: '',
})

//處理表單送出
const handleSubmit = () => {
  if (form.value.name && form.value.price) {
    if (form.value.id) {
      const target = products.value.find((p) => p.id === form.value.id)
      target.name = form.value.name
      target.price = form.value.price
    } else {
      products.value.push({ id: nextId++, name: form.value.name, price: form.value.price })
    }
  }
}

//重製表單
const resetForm = () => {
  form.value = {
    id: null,
    name: '',
    price: '',
  }
}

//編輯商品
const editProduct = () => {}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: auto;
}
form {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 1rem;
}
input {
  padding: 6px;
}
button {
  padding: 6px 12px;
}
</style>
