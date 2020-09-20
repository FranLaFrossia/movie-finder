<template>
  <div class="wrapper --main movie-list">
    <nuxt-link to="/" class="back">
      Go back to search for more awesome movies by title
    </nuxt-link>
    <div class="title">
      Results for: "{{ this.$route.params.movies }}"
    </div>
    <MovieSlider v-if="movies" :movies="movies.Search" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      movies: ''
    }
  },
  mounted () {
    this.searchMovies()
  },
  methods: {
    async searchMovies () {
      const slug = this.$route.params.movies
      const url = `http://www.omdbapi.com/?s=${slug}&apikey=18fbdd39&type=movie`
      const movies = await this.$axios.$get(url)
      this.movies = movies
    }
  }
}
</script>

<style scoped>
.back {
  margin-top: 0.5em;
  display: block;
}
.title {
  font-size: 1.3rem;
  margin-top: 1.5em;
}
</style>

<style>
.movie-slider {
  max-width: 600px;
  margin: 0 auto;
}
</style>
