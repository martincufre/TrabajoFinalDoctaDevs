<template>
    <div>
        <lista-posts :URL="URL"></lista-posts>
    </div>
</template>

<script>
import ListaPosts from "@/components/ListaPosts";

export default {
    name: "PostSingle",
    data() {
        return {
            URL:`https://node-api-doctadevs.vercel.app/users/${this.$route.params.idPost}/posts`
        }
    },
}
</script>