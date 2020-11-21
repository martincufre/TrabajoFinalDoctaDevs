<template>
    <div class="boton">
        <button @click="eliminarUser">Eliminar</button>
    </div>
</template>

<script>
export default {
    name: 'BotonEliminarCuenta',
    methods: {
        eliminarUser(){
            this.$emit('eliminar-usuario')
        }
    },
}
</script>

<style>

</style>