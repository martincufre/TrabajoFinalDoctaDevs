<template>
    <div class="formulario">
        <h2>Registrarse</h2>
        <form action="">
            <input type="text" placeholder="Nombre" v-model="nombre">
            <input type="text" placeholder="Username" v-model="username">
            <input type="password" placeholder="Password" v-model="password">
            <button @click.prevent="registrar">Registrarse</button>

            <p>{{mensaje}}</p>
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
            this.nombre = '';
            this.username = '';
            this.password = '';

            this.mensaje = "Usuario registrado con éxito, para ingresar a DoctaTweets dirígete a Login";
        }
    },
}
</script>

<style>
    .formulario{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        min-height: 50vh;
    }
    .formulario input{
        width: 90%;
        height: 35px;
        margin: 10px 0;
        border: 1px solid #cccccc;
        border-radius: 5px;
        font-size: 1rem;
    }
    .formulario button{
    width: 30%;
    height: 45px;
    margin: 10px 0;
    border-radius: 5px;
    font-size: 1rem;
    }
    @media screen and (max-width: 730px) {
        .formulario{
            width: 80%;
            height: 350px;
            margin: 15px auto;
        }
        .formulario form{
            margin: 0 auto;
        }
    }    
</style>