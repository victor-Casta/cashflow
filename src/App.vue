<script>
  import SplashScreen from './components/SplashScreen.vue'; 
  import { defineAsyncComponent } from 'vue';

  export default {
    components: {
      SplashScreen,
      Home: defineAsyncComponent(
        () => new Promise((resolve) => {
          setTimeout(() => {
            resolve(import('./components/Home.vue'))
          }, 2000)
        })
      )
    }
  }
</script>

<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<style scoped>
</style>
