<template>
  <div>
    <menu-app></menu-app>
    <header-app></header-app>
    <footer-app></footer-app>
    <router-view></router-view>
  </div>
</template>

<script>
import MenuApp from "@/components/MenuApp.vue"
import HeaderApp from '@/components/HeaderApp.vue'
import FooterApp from '@/components/FooterApp.vue'

export default {
  name: 'App',
  components: {
        HeaderApp,
        FooterApp,
        MenuApp
        },
}
</script>
