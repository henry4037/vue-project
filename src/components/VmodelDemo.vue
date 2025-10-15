<script setup>
import { ref } from 'vue'

const gender = ref('')
const country = ref('')
const countries = ref([
  { numeric: 158, code: 'TW', name: '台灣' },
  { numeric: 392, code: 'JP', name: '日本' },
  { numeric: 840, code: 'US', name: '美國' },
  { numeric: 410, code: 'KR', name: '韓國' },
  { numeric: 156, code: 'CN', name: '中國' },
  { numeric: 826, code: 'UK', name: '英國' },
  { numeric: 250, code: 'FR', name: '法國' },
  { numeric: 276, code: 'DE', name: '德國' },
])
</script>

<template>
  <div class="gender-radio">
    <h3>選擇性別：</h3>
    <div class="selections">
      <label><input type="radio" value="男生" v-model="gender" />男生</label>
      <label><input type="radio" value="女生" v-model="gender" />女生</label>
    </div>

    <div class="result">
      <p>你選擇的性別：{{ gender }}</p>
    </div>
  </div>

  <div class="nationality">
    <h3>選擇國籍 :</h3>
    <div class="selections">
      <select class="selections" v-model="country">
        <option disabled value="">未選國籍</option>
        <option v-for="country in countries" :key="country.numeric" :value="country.numeric">
          {{ country.name }}
        </option>
      </select>
    </div>

    <div class="result">
      <p>國家代碼 : {{ country }}</p>
    </div>
  </div>
</template>

<style scoped></style>
