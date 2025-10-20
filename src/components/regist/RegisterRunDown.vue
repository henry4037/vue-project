<script setup>
import { ref, computed } from 'vue'

import Step1 from './Step1.vue'
import Step2 from './Step2.vue'
import Step3 from './Step3.vue'

const steps = [Step1, Step2, Step3]
const currentStep = ref(0)
const currentStepComponent = computed(() => steps[currentStep.value])

const errorMessage = ref('')

const form = ref({
  name: '',
  email: '',
})

const nextStep = () => {
  errorMessage.value = ''

  if (currentStep.value === 0 && !form.value.name) {
    errorMessage.value = '請輸入姓名'
    return
  }
  if (currentStep.value === 1 && !form.value.email) {
    errorMessage.value = '請輸入信箱'
    return
  }
  if (currentStep.value < steps.length - 1) {
    currentStep.value++
  } else {
    alert(` 表單送出：${JSON.stringify(form.value)}`)
  }
}

const prevStep = () => {
  if (currentStep.value > 0) {
    errorMessage.value = ''
    currentStep.value--
  }
}
</script>

<template>
  <div class="form-container">
    <h3>步驟 {{ currentStep + 1 }} / {{ steps.length }}</h3>

    <transition name="fade" mode="out-in">
      <component :is="currentStepComponent" :form="form" :key="currentStep" />
    </transition>

    <p class="error" v-if="errorMessage">{{ errorMessage }}</p>

    <div class="actions">
      <button @click="prevStep" :disabled="currentStep === 0">⬅ 上一步</button>
      <button @click="nextStep">
        {{ currentStep === steps.length - 1 ? ' 送出' : '➡ 下一步' }}
      </button>
    </div>
    <!-- <pre>{{ form }}</pre> -->
  </div>
</template>

<style scoped>
.form-container {
  max-width: 400px;
  margin: 2rem auto;
  padding: 1.5rem;
  border: 1px solid #ccc;
  border-radius: 10px;
  background: #fdfdfd;
}

input {
  width: 100%;
  padding: 0.5rem;
  margin: 1rem 0;
  border-radius: 6px;
  border: 1px solid #ccc;
}

.actions {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}

button {
  padding: 0.4rem 1rem;
  border: none;
  border-radius: 6px;
  background: #42b983;
  color: white;
  cursor: pointer;
}

button:disabled {
  background: #aaa;
}

.error {
  color: red;
  font-size: 0.9rem;
  margin-top: 0.5rem;
}

/* ✨ 加入動畫 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
