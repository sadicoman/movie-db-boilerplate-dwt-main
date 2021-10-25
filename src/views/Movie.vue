<template>
  <div class="movie-detail">
    <h1>This is the Movie detail page</h1>
    <h2>This movie id is : {{ id }}</h2>
  </div>
</template>

<script>
import { useRoute } from 'vue-router'
import { onMounted } from 'vue'

export default {
  name: 'About',
  components: {
  },
  setup () {
    // Accéder à la variable `route`
    const route = useRoute()
    // Récupérer le paramètre `id` passé dans l'url
    const id = route.params.id

    // Décommenter les deux lignes ci-dessous
    // const baseUrl = 'https://api.themoviedb.org/3'
    // const endpoint = `${baseUrl}/movie/INSERER_ID_ICI?api_key=${process.env.VUE_APP_API_KEY}`

    onMounted(() => {
      // faire le fetch ici
    })

    return {
      id
    }
  }
}
</script>
