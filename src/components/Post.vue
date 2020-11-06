<template>
    <div>
        
    </div>
</template>

<script>
export default {
    name: "Post",
    data() {
        return {
            post: {},
        }
    },
    props: {
        autor: String,
        fecha: String,
        mensaje: String,
        likes: Number
    }
}
</script>