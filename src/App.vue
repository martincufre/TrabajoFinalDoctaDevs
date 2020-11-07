<template>
  <div>
    <home></home>
    <registro></registro>
    <login></login>
    <router-view></router-view>
  </div>
</template>

<script>
import Home from '@/views/Home.vue'
import Registro from '@/views/Registro.vue'
import Login from '@/views/Login.vue'
export default {
  name: 'App',
  components: {
        Home,
        Registro,
        Login
        },
}
</script>
