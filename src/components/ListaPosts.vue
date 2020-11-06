<template>
    <div>
        <post v-for="(post, tweet) in posts" :key="tweet"
        :autor="post.autor.username"
        :fecha='post.fecha'
        :mensaje='post.mensaje'
        :likes='post.likes.length'
        ></post>
    </div>
</template>

<script>
import Post from './Post'

export default {
    name: "ListaPost",
    components:{
        Post,
    },
    created() {
        fetch("https://node-api-doctadevs.vercel.app/posts")
        .then(response => response.json())
        .then(result => {
            if(result.error) return console.log(result);

            this.posts=result.body;
            return true;
            })
        .catch(error => console.log('error', error));
    },
    data() {
        return {
            posts: [],
        }
    },
    
}
</script>