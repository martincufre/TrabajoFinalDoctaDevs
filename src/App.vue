<template>
  <div>
    <post></post>
    <lista-posts></lista-posts>
  </div>
</template>

<script>
import Post from "@/components/Post";
import ListaPosts from "@/components/ListaPosts";
export default {
  name: 'App',
  components: {
          Post,
          ListaPosts
        },
}
</script>
