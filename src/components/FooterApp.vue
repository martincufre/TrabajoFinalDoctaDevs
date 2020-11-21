<template>
    <div class="footer">
        <p class="texto">Doctatweets 2020 todos los derechos reservados</p>
        <p class="texto">Términos y Condiciones</p>
        
    </div>
</template>

<script>
export default {
    name: 'FooterApp'
}
</script>

<style>
    .footer{
        background-color: #3399FF;
        color: #3399FF;
        padding: 3px;
    }
    .texto{
        color: cornsilk;
        text-align: center;
    }
    @media screen and (max-width: 750px) {
        .footer{
            height: 100px;
            width: 100%;
            font-size: 0.9rem;
            
        }
    }    
</style>