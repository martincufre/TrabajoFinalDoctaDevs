<template>
    <div>
        <p>Ingresar<p>
        <form>
            <input type="text" placeholder="Usuario" v-model="usuario">
            <input type="password" placeholder="Password" v-model="password">
            <button @click.prevent="ingreso">Login</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'FormularioLogin',
    data() {
        return {
            usuario: '',
            password: ''
        }
    },
    methods: {
        ingreso(){
            fetch('https://node-api-doctadevs.vercel.app/users/{{USERNAME}}')
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
