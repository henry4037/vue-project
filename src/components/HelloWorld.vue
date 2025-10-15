<script setup>
// eslint-disable-next-line no-unused-vars
const props = defineProps({
  msgText: {
    type: String,
    required: true,
  },

  msgText2: {
    type: String,
    required: true,
  },

  msg: {
    type: String,
  },

  defaultLower: { type: String, default: 'default' },

  propF: {
    type: Object,
    default() {
      return { message: 'hello world' }
    },
  },
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vite.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
