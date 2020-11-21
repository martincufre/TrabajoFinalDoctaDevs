<template>
    <div>
        <h2>Ingresar</h2>
        <form class="formlogin">
            <input type="text" placeholder="Usuario" v-model="usuario">
            <input type="password" placeholder="Password" v-model="password">
            <button @click.prevent="ingreso">Login</button>
            <span>Si no estas suscripto <a href="./registro">Regístrate</a></span>
            
            <span><strong>{{error}}</strong></span>
        </form>
    </div>
</template>

<script>
export default {
    name: 'FormularioLogin',
    data() {
        return {
            usuario: '',
            password: '',
            error: '',
        }
    },
    methods: {
        ingreso(){
            fetch('https://node-api-doctadevs.vercel.app/login',
            {
                method: 'POST',
                headers: {'Content-Type':'application/json'},
                body: JSON.stringify(
                        {
                        username: this.usuario,
                        password: this.password,
                        })
            })
            .then(res => {
                return res.json()
            })
            .then(result => {
                if (result.error){
                    this.error = result.message;
                    return
                } 
                sessionStorage.setItem("token", result.body.token);
                sessionStorage.setItem('username', this.usuario);
                this.username = "";
                this.password = "";

                this.$router.push({name: "Home"}); 
            })
            .catch(err => {
                console.log(err)
            })


        }
        
    },


        


}
</script>

<style>
    h2{
        color: black;
        text-align: center;
        font-size: 2rem;
    }
    .formlogin{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 10px auto;
        padding: 10px;
        }
    .formlogin input{
        width: 70%;
        height: 45px;
        margin: 10px 0;
        border: 1px solid #cccccc;
        border-radius: 5px;
        font-size: 1rem;
    }
    .formlogin button{
        width: 30%;
        height: 45px;
        margin: 10px 0;
        border: 1px solid #cccccc;
        border-radius: 5px;
        font-size: 1.5rem;
    }
    @media screen and (max-width: 730px) {
        .formlogin{
            width: 80%;
            height: 350px;
            margin: 15px auto;
        }
        .formlogin form{
            margin: 0 auto;
        }
    }    
</style>
