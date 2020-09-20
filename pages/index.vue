<template>
  <div class="wrapper --main">
    <h1 class="page-title">
      Movie Finder
    </h1>
    <SearchBox @searchValue="searchMovie" />
    <p v-for="(movie) in movies.Search" :key="movie.index">
      {{ movie.Title }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      movies: ''
    }
  },
  methods: {
    searchMovie (val) {
      this.$router.push({ name: 'movies', params: { movies: val } })
    }
  }
}
</script>

<style lang="css" scoped>
.wrapper {
  min-height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.page-title {
  margin-bottom: 1.5rem;
}
</style>
