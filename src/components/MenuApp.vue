<template>
    <div class="menu">
        <router-link class="ruta" :to="{path:'/'}">Login</router-link>
        <router-link class="ruta" :to="{path:'/registro'}">Registro</router-link>
        <router-link class="ruta" :to="{name:'Home'}">Home</router-link>
        <router-link class="ruta" :to="{path:'Feed'}">Feed</router-link>
        <router-link class="ruta" :to="{path:'Perfil'}">Perfil</router-link>
        
    </div>
</template>

<script>
export default {
    name: 'MenuApp',

}
</script>

<style>
    .menu{
        text-align: end;
    }
    .ruta{
        color: #ffffff;
        padding: 0 15px;
        text-decoration: none;
        font-size: 1.2rem;
    }
    .ruta:hover{
        background-color: royalblue;
    }
</style>