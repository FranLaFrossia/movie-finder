<template>
  <div class="movie-slider">
    <div
      class="arrow --left"
      :class="{'invisible': ! hasPrev()}"
      @click.stop="prev"
    >
      <svg
        fill="#222222"
        height="48"
        viewBox="0 0 24 24"
        width="48"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M15.41 16.09l-4.58-4.59 4.58-4.59L14 5.5l-6 6 6 6z" />
        <path d="M0-.5h24v24H0z" fill="none" />
      </svg>
    </div>
    <div class="image-wrapper" @click.stop>
      <div class="movie-info">
        <p>{{ movies[index].Title }}</p>
        <p>{{ movies[index].Year }}</p>
      </div>
      <img :src="movies[index].Poster" :alt="movies[index].Title">
    </div>
    <div
      class="arrow --right"
      :class="{'invisible': ! hasNext()}"
      @click.stop="next"
    >
      <svg
        fill="#222222"
        height="48"
        viewBox="0 0 24 24"
        width="48"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M8.59 16.34l4.58-4.59-4.58-4.59L10 5.75l6 6-6 6z" />
        <path d="M0-.25h24v24H0z" fill="none" />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MoviesSlider',
  props: {
    movies: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      visible: false,
      index: 0
    }
  },
  methods: {
    // Evaluates if there's more movies in the array
    hasNext () {
      return this.index + 1 < this.movies.length
    },
    hasPrev () {
      return this.index - 1 >= 0
    },
    // Show previous movie on array
    prev () {
      if (this.hasPrev()) {
        this.index -= 1
      }
    },
    // Show next movie on array
    next () {
      if (this.hasNext()) {
        this.index += 1
      }
    },
    setIndex (i) {
      this.index = i
    }
  }
}
</script>

<style scoped>
.movie-slider {
  display: grid;
  grid-template-columns: 48px auto 48px;
  width: 100%;
  margin-top: 2rem;
}
  .image-wrapper {
    text-align: center;
  }
    .movie-info {
      margin: 0 0 1.5rem;
    }
    .poster {
      display: block;
      margin: 0 auto;
    }
.arrow {
  cursor: pointer;
  align-self: center;
}
  .arrow svg {
    pointer-events: none;
  }
.invisible {
  visibility: hidden;
}
</style>
