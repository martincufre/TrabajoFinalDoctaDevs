<template>
    <div>
        <p>Registrarse</p>
        <form action="">
            <input type="text" placeholder="Nombre" v-model="nombre">
            <input type="text" placeholder="Username" v-model="username">
            <input type="password" placeholder="Password" v-model="password">
            <button @click.prevent="registrar">Registrarse</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'FormularioUsuario',
    data() {
        return {
            nombre: '',
            username: '',
            password: ''
        }
    },
    methods: {
        registrar(){
            fetch('https://node-api-doctadevs.vercel.app/users',
            {
                method: 'POST',
                headers: {'Content-Type':'application/json'},
                body: JSON.stringify({
                    "name": this.nombre,
                    "username": this.username,
                    "password": this.password
                })
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