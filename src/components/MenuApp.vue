<template>
    <div class="menu">
        <router-link class="ruta" :to="{path:'/', name: 'Login'}">Login</router-link>
        <router-link class="ruta" :to="{path:'/registro'}">Registro</router-link>
        <router-link class="ruta" :to="{path:'/home', name:'Home'}">Home</router-link>
        <router-link class="ruta" :to="{path: '/feed' , name: 'Feed', params: {username: username}}">Feed</router-link>
        <router-link class="ruta" :to="{path:'/home', name:'Perfil'}">Perfil</router-link>
        
    </div>
</template>

<script>
export default {
    name: 'MenuApp',
    data() {
        return{
            username: window.sessionStorage.getItem('username')
        }
    },
watch: {
        $route() {
            this.username = sessionStorage.getItem('username');
        }
    },

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

    @media screen and (max-width: 730px) {
        .menu{
            height: 50px;
            display: flex;
            flex-flow: column;
        }
    }
</style>