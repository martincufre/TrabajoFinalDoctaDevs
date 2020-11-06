<template>
    <div class="boton__eliminar__post">
        <button @click="eliminarPost">Eliminar</button>
    </div>
</template>

<script>
export default {
    name: 'BotonEliminarPost',
    methods: {
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
    },
}
</script>