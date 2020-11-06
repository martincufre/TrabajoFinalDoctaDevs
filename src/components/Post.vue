<template>
    <div>
        <div>
            <h2>{{autor}}</h2>
            <p>{{fecha}}</p>
            <p>{{mensaje}}</p>   
            <boton-like>{{likes}}</boton-like>
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
    }
}
</script>