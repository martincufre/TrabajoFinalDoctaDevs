<template>
    <div class="perfil">
        <div class="titulos">
            <h1><i class="far fa-user-circle"></i></h1>
            <h3>{{`Nombre: ${nombre}`}}</h3>
        </div>
        <div class="info">
            <p>{{`Usuario: ${usuario}`}}</p>
            <p>{{`Rol: ${rol}`}}</p>
        </div>
        
        <boton-eliminar-cuenta @eliminar-usuario="eliminarUser" class="botonEliminar"></boton-eliminar-cuenta>
        
    </div>
</template>

<script>
import BotonEliminarCuenta from '@/components/BotonEliminarCuenta'

export default {
    name: 'Perfil',
    components: {
        BotonEliminarCuenta
    },
    data() {
        return {
            nombre: '',
            usuario: '',
            rol: ''
        }
    },
    created() {
        fetch(`https://node-api-doctadevs.vercel.app/users/${sessionStorage.getItem('username')}`,{
            headers: {
                'Accept': 'application/json',
                'Content-Type':'application/json',
                'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
            },
        })
        .then(res => res.json())
        .then(data => {
            this.nombre = data.body.name
            this.usuario = data.body.username
            this.rol = data.body.role
        })
        .catch(err => console.log(err))
    },
    methods: {
        eliminarUser(){
            fetch(`https://node-api-doctadevs.vercel.app/users/${sessionStorage.getItem('username')}`,{
                headers: {
                    'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
                },
                method: 'DELETE',
                body: {
                    autor: sessionStorage.getItem('username')
                    }
            })
            .then(res => {
                return res.json()
                })
            .then(data => {
                console.log(data)
                sessionStorage.removeItem('token')
                sessionStorage.removeItem('username')
                this.$router.push({name: 'Login'})
            })
            .catch(err => console.log(err))
        },
    },
}
</script>

<style>
    .perfil{
        width: 200px;
        margin: 10px auto;
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        align-items: center;
    }
    .titulos h1{
        font-size: 12rem;
        margin: 0;
        color: black;
    }
    .info{
        flex-basis: 90%;
        margin: 10px auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .botonEliminar{
        margin-left: 400px;
        text-align: end;
    }
</style>
