<template>
    <div class="menu">
        <router-link class="ruta" :to="{path:'/'}">Login</router-link>
        <router-link class="ruta" :to="{path:'/registro'}">Registro</router-link>
        <router-link class="ruta" :to="{path:'/home', name:'Home'}">Home</router-link>
        <router-link class="ruta" :to="{path: '/feed' , name: 'Feed', params: {username: usuarioLogueado}}">Feed</router-link>
        <router-link class="ruta" :to="{path:'/home', name:'Perfil'}">Perfil</router-link>
        
    </div>
</template>

<script>
export default {
    name: 'MenuApp',
    data() {
        return{
            usuarioLogueado: sessionStorage.getItem('username')
        }
    }

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