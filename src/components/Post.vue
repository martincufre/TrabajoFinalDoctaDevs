<template>
    <div>
        <div>
            <h2>{{autor}}</h2>
            <p>{{fecha}}</p>
            <p>{{mensaje}}</p>   
            <boton-like @event-like="likePost">{{likes}}</boton-like>
            <boton-eliminar-post></boton-eliminar-post>
        </div>
    </div>
</template>

<script>
import BotonEliminarPost from './BotonEliminarPost'
import BotonLike from './BotonLike'


export default {
    name: 'Post',
    components: {
        BotonEliminarPost,
        BotonLike,
    },
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