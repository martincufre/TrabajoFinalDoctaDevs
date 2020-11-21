<template>
    <div class="post">
        <div class="titulo">
            <h3>{{this.autor}}</h3>
            <span>{{this.fecha}}</span>
        </div>
        <div class="mensaje"> 
            <p>{{this.mensaje}}</p>
        </div>
        <div class="botones">          
            <boton-eliminar-post :idPostUsuario='idPost' @postDelete="eliminarPost" v-if="username == autor"></boton-eliminar-post>
            <boton-like :idPostUsuario='idPost' @event-like="likePost" @click="likePost"></boton-like>{{this.likes}}
        </div>
    </div>
</template>

<script>

import BotonLike from '@/components/BotonLike'
import BotonEliminarPost from '@/components/BotonEliminarPost'

export default {
    name: 'Post',
    components: {
        BotonLike,
        BotonEliminarPost
    },
    data() {
        return {
            post: {},
            username: sessionStorage.getItem('username')
        }
    },
    props: {
        autor: String,
        fecha: String,
        mensaje: String,
        likes: Number,
        idPost: String
    },
    methods: {
        likePost(){
            fetch(`https://node-api-doctadevs.vercel.app/posts/${this.idPost}/like`,
            {
                headers: {
                    'Accept': 'application/json',
                    'Content-Type':'application/json',
                    'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
                    },
                    method: 'POST'
                })
                .then(res => {
                    return res.json()
                })
                .then(data => {
                    console.log(data)
                    this.$emit('like')
        
                })
                .catch(err => console.log(err));
            },

        eliminarPost(){
            fetch(`https://node-api-doctadevs.vercel.app/posts/${this.idPost}`, {
            headers: {
                'Accept': 'application/json',
                'Content-Type':'application/json',
                'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
                },
                method: 'DELETE',
                body: JSON.stringify({
                    autor: sessionStorage.getItem('username')
                    })
            })
            .then(res => {
                return res.json()
                })
            .then(data => {
                console.log(data)
                this.$emit('eliminar')
            })
            .catch(err => console.log(err))
        },
}
}   

</script>

<style>
    .post{
        width: 600px;
        margin: 10px auto;
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        align-items: center;
        min-height: 10vh;
        text-transform: lowercase;
        cursor: pointer;
    }
    .post .titulo{
        margin: 10px;
        flex-basis: 100%;
        display: flex;
        align-items: baseline;
    }
    .post h3{
        margin: 10px;
        padding-left: 10px;
    }
    .post .mensaje{
        flex-basis: 100%;
        margin: 10px 30px;
    }
    .post .botones{
        display: flex;

    }
    .post .titulo h3{
        width: 60%;
    }
    @media screen and (max-width: 730px) {
        .post{
            margin: 10px;
            margin-bottom: 10px;
            font-size: 0.9rem;
        }
        .post .titulo{
            font-size: 0.71rem;
            margin-block-end:15px;
            margin-left: 2px;
        }
        .post .mensaje{
            font-size: 0.9rem;
            
        }
        .post .botones{
            font-size: 0.8em;
        }
    }
</style>