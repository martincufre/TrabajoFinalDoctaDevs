<template>
    <div >
        <button @click="eliminarUser">Eliminar cuenta</button>
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