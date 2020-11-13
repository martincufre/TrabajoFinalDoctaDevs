<template>
    <div>
        <post v-for="(post, tweet) in posts" :key="tweet"
        :autor="post.autor.username"
        :fecha='post.fecha'
        :mensaje='post.mensaje'
        :likes='post.likes.length'
        :idPost='post._id'
        :postURL="postURL"
        @like="getPosts"></post>
    </div>
</template>

<script>
import Post from '@/components/Post'

export default {
    name: "ListaPosts",
    props: {
        URL: String
    },
    components:{
        Post,
    },
    methods: {
        getPosts(){
            fetch(this.postURL)
            .then(response => response.json())
            .then(data => {
                this.posts = data.body;
            })
            .catch(err => console.log(err));
        },
        created() {
            this.getPosts()
        }, 
        data() {
            return {
                posts: [],
                postURL: "https://node-api-doctadevs.vercel.app/posts"
            }
    }

    }
}

</script>