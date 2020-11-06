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
            fetch(`https://node-api-doctadevs.vercel.app/posts/{{POST_ID}}/like`,
            {
                method: 'POST'
            })
            .then(res => {
                return res.json()
            })
            .then(data => {
                console.log(data)
            })
            .catch(err => {
                console.log(err)
            })
        }
    },    
}
</script>