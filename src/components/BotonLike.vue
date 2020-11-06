<template>
    <div>
        <button @click="likePost">Like</button>
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