<template>
    <div>
        <formulario-publicacion></formulario-publicacion>
        <lista-posts></lista-posts>
    </div>
</template>

<script>
import FormularioPublicacion from '@/components/FormularioPublicacion'
import ListaPosts from '@/components/ListaPosts'

export default {
    name: 'Feed',
    components: {
        FormularioPublicacion,
        ListaPosts
    }
}
</script>