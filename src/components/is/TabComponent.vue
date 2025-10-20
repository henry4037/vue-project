<script setup>
import { ref, computed } from 'vue'

import home from './Home.vue'
import contact from './Contact.vue'
import about from './About.vue'

const tabs = ['home', 'contact', 'about']
const currentTab = ref('home')

const componentMap = {
  home,
  contact,
  about,
}

const currentTabComponent = computed(() => componentMap[currentTab.value])
</script>

<template>
  <div class="tabs">
    <button v-for="tab in tabs" :key="tab" @click="currentTab = tab">
      {{ tab }}
    </button>
  </div>

  <component :is="currentTabComponent" class="content" />
</template>

<style scoped>
.tabs {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

button {
  padding: 0.5rem 1rem;
  cursor: pointer;
  border-radius: 6px;
  border: none;
  background: #42b983;
  color: white;
}

.content {
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}
</style>
