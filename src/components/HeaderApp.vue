<template>
<div>
        <div class="encabezado">
            <div>
            <menu-app class= "menu"></menu-app>
            </div>
            <h1>DOCTATWEETS</h1>
            <boton-cerrar-sesion class="cerrar"></boton-cerrar-sesion>
        </div>
</div>
</template>

<script>
import MenuApp from "@/components/MenuApp.vue";
import BotonCerrarSesion from "@/components/BotonCerrarSesion.vue";
export default {
    name: 'HeaderApp',
    components: {
        MenuApp,
        BotonCerrarSesion
    }
}
</script>

<style>
    .encabezado{
        background-color: #3399FF;
        color: #3399FF;
        padding: 15px;
    }
    .encabezado h1{
        display: flex;
        justify-content: center;
        color: whitesmoke;
    }

</style>