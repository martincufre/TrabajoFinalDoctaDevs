<template>
  <div>
    <menu-app></menu-app>
    <header-app></header-app>
    <footer-app></footer-app>
    <router-view @load-list=" cargarLista"></router-view>

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

  methods: {
     cargarLista(){
        fetch("https://node-api-doctadevs.vercel.app/posts")
            .then(response => response.json())
            .then(result => {
                if(result.error) return console.log(result);

                this.posts=result.body;
                return true;
                })
            .catch(error => console.log('error', error));
        }
    },      
}
</script>
