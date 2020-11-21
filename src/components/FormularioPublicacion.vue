<template>
    <div class="formPublic">
        <form @submit.prevent="publicarPost" >
            <h4>Actividad</h4>
            <textarea class="public" v-model="publicar" placeholder="¿Que está pasando?"></textarea>
            <button>Publicar</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'FormularioPublicacion',
    data() {
        return {
            publicar: '',
        }
    },
    methods: {
        publicarPost() {
            fetch('https://node-api-doctadevs.vercel.app/posts',
                {
                method: 'POST',
                headers:
                {
                    'Accept': 'application/json',
                    'Content-Type':'application/json',
                    'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
                },
                body: JSON.stringify({
                        autor: sessionStorage.getItem('username'),
                        mensaje: this.publicar
                    }
                )
                }
            )
            .then(res => {
                return res.json()
            })
            .then(data => {
                console.log(data)
            })
            .catch(err => {
                console.log(err)
            })
            this.publicar = ''
        },
    },
}
</script>

<style>
    .formPublic h4{
        text-align: center;
        font-size: 1.5rem;
        margin: 5px;
    }
    .formPublic .public{
        width: 700px;
        margin: 20px auto;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 10vh;
        border: 1px solid black;
        border-radius: 5px;
        flex-flow: row wrap;
        color: black;
        cursor: pointer;
    }
    .formPublic button{
        font-size: 1rem;
        color: whitesmoke;
        border: none;
        margin: 5px 0;
        padding: 5px;
        margin-left: 60px
        
    }
    @media screen and (max-width: 730px) {
        .formPublic{
            width: 80%;
            height: 100px;
            margin-bottom: 100px;
            display: flex;
            justify-content: center;
        }
        .formPublic .public{
            width: 165%;
            height: 50px;
            margin-left: 8px;
        }
        .formPublic button{
            width: 50%;
            height: 30px;
        }
    }
</style>