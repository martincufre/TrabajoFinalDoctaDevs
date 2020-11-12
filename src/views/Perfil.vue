<template>
    <div>
        <h2>{{`Nombre: ${nombre}`}}</h2>
        <div>
            <p>{{`Usuario: ${usuario}`}}</p>
            <p>{{`Rol: ${rol}`}}</p>
        </div>
        <boton-eliminar-cuenta @event-eliminar="eliminarUser"></boton-eliminar-cuenta>
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
                    'Accept': 'application/json',
                    'Content-Type':'application/json',
                    'Authorization' : `Bearer ${sessionStorage.getItem('token')}`
                },
                method: 'DELETE',
                body: {
                    autor: this.autor
                    }
            })
            .then(res => {
                return res.json()
                })
            .then(data => {
                console.log(data)
            })
            .catch(err => console.log(err))
        },
    },
}
</script>
