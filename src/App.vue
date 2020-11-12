<template>
  <div>
    <header-app></header-app>
    <router-view></router-view>
    <footer-app></footer-app>
    

  </div>
</template>

<script>

import HeaderApp from '@/components/HeaderApp.vue'
import FooterApp from '@/components/FooterApp.vue'

export default {
  name: 'App',
  components: {
        HeaderApp,
        FooterApp,
        },
      
}
</script>

<style>
  html{
        font-family: Arial, Helvetica, sans-serif;
    }
</style>