<template>
    <div>
        <div>
            <h2>{{this.autor}}</h2>
            <p>{{this.fecha}}</p>
            <p>{{this.mensaje}}</p>   
            <boton-like @event-like="likePost"></boton-like>
            <boton-eliminar-post @event-eliminar="eliminarPost"></boton-eliminar-post>
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
    eliminarPost(){
        fetch(`https://node-api-doctadevs.vercel.app/posts/{{POST_ID}}`, 
            {
                method: 'DELETE',
                body: {
                    "autor": "USERNAME"
            }
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
}   

</script>