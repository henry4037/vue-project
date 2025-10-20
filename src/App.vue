<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TabComponent from './components/is/TabComponent.vue'
import ProductManager from './components/ProductManager.vue'
import RefComponent from './components/RefComponent.vue'
import RegisterRunDown from './components/regist/RegisterRunDown.vue'
import TheWelcome from './components/TheWelcome.vue'
import VmodelDemo from './components/VmodelDemo.vue'
import WatchEffectComp from './components/WatchEffectComp.vue'
import WatchRef from './components/WatchRef.vue'
import ProductPage from './components/product/ProductPage.vue'

const hzn = "hzn's"
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld :msg="hzn" />
    </div>
  </header>

  <main>
    <!-- <TheWelcome /> -->
    <!-- <ProductManager /> -->
    <!-- <VmodelDemo /> -->
    <!-- <RefComponent /> -->
    <!-- <WatchRef /> -->
    <!-- <WatchEffectComp /> -->
    <!-- <RegisterRunDown /> -->
    <ProductPage />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
