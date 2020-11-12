<template>
    <div>
        <button @click="likePost"><i class="far fa-heart"></i></button>
    </div>
</template>

<script>
export default {
    name: 'BotonLike',
    methods: {
       likePost(){
       this.$emit('event-like')
       }
    },
}
</script>

<style scoped>
    button{
        border: none;
        background-color: white;
        color: black;
        font-size: 20px;
        cursor: pointer;
    }
    button:hover{
        background-color: #ee8989;
        color: #e22727;
    }
</style>