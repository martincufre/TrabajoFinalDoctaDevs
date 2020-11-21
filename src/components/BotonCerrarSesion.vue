<template>
    <div>
        <button @click.prevent="cerrarSesion">Cerrar Sesion</button>
    </div>
</template>

<script>
export default {
    name: 'BotonCerrarSesion',
    methods: {
        cerrarSesion(){
            sessionStorage.removeItem('token')
            sessionStorage.removeItem('username')
            this.$router.push({name: "Login"})
        }
    },
}
</script>

<style>
    button{
        background-color: #3399FF;
        color: seashell;
        border-radius: 5px;
        border: seashell 1px solid;
    }
</style>