<template>
  <div class="home">
    <h1>This is the Homepage</h1>
    <!-- Exemple de lien à utiliser pour lier vos cards à la page `Movie` -->
    <RouterLink to="/movie/12345">Exemple de lien vers la page movie</RouterLink>
  </div>
  <ul v-if="data">
    <!-- <li v-for="(movie, index) in data.results" :key="index">{{ movie }}</li> -->
    <MovieCard
      v-for="(movie, index) in data.results"
      :key="index"
      :poster="movie.poster_path"
      :title="movie.title"
      :score="movie.vote_average"
      :id="movie.id"
    >
    </MovieCard>
  </ul>

</template>

<script>
import { onMounted, ref } from 'vue'
import MovieCard from '../components/MovieCard.vue'

export default {
  name: 'Home',
  components: {
    MovieCard
  },
  setup () {
    // Décommenter les deux lignes ci-dessous
    const baseUrl = 'https://api.themoviedb.org/3'
    const endpoint = `${baseUrl}/discover/movie?primary_release_year=2021&sort_by=popularity.desc&api_key=${process.env.VUE_APP_API_KEY}`

    const data = ref(null)

    onMounted(() => {
      // faire le fetch ici
      fetch(endpoint)
        .then(res => {
          return res.json()
        })
        .then(res => (
          data.value = res
        ))
    })

    /*
      NOTE: Pour affichier la cover pour chaque films vous aurez
      une propriété `poster_path` qui ressembler à un truc comme ça:
      `/o9iYeSBx7lwWRDEt8QPWbKZZlJm.jpg`

      Pour afficher cette image, préfixez `poster_path`avec:
      `https://image.tmdb.org/t/p/w300/`

      Voir la doc: https://developers.themoviedb.org/3/getting-started/images
    */

    return {
      data,
      MovieCard
    }
  }
}
</script>
