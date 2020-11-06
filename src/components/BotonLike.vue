<template>
    <div>
        <button @click="likePost">Like</button>
    </div>
</template>

<script>
export default {
    name: 'BotonLike',
    data() {
        return {
            like: 0,
        }
    },
    methods: {
       likePost(){
       this.$emit('event-like')
       }
    },
}
</script>