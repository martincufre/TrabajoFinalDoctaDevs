<template>
    <div class="menu">
        <router-link class="ruta" to="Login">Login</router-link>
        <router-link class="ruta" to="Registro">Registro</router-link>
        <router-link class="ruta" to="/">Home</router-link>
        
    </div>
</template>

<script>
export default {
    name: 'MenuApp',

}
</script>

<style>
    .ruta{
        color: gray;
    }
</style>