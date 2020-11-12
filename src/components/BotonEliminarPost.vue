<template>
    <div>
        <button @click="eliminarPost"><i class="fas fa-trash-alt"></i></button>
    </div>
</template>

<script>
export default {
    name: 'BotonEliminarPost',
    methods: {
        eliminarPost(){
            this.$emit('postDelete')
        }
    },
}
</script>

<style scoped>
    button{
        border: none;
        background-color: white;
        font-size: 20px;
        color: black;
        cursor: pointer;
    }
    button:hover{
        background-color: #ad5656;
        color: #881414;
    }
</style>