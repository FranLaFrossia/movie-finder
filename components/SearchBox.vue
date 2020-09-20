<template>
  <div class="search-box">
    <input
      v-model="search"
      class="search-input"
      placeholder="Search movies by title"
      type="text"
      autofocus
      @keyup.enter="submitSearch"
    >
    <button class="search-btn btn --primary" @click="submitSearch">
      Find
    </button>
  </div>
</template>

<script>
export default {
  name: 'SearchBox',
  data () {
    return {
      search: ''
    }
  },
  methods: {
    submitSearch () {
      this.$emit('searchValue', this.search)
    }
  }
}
</script>

<style scoped>
.search-box {
  display: grid;
  column-gap: 1.2rem;
  grid-template-columns: auto 8rem;
  max-width: 600px;
  width: 90%;
}

.search-input {
  width: 100%;
  height: 40px;
  font-size: 1.1rem;
  padding: 0.5rem;
}

.search-btn {
  display: block;
  width: 100%;
}
  @media (max-width: 550px) {
    .search-box {
      display: block;
    }
    .search-btn {
      margin-top: 1.5rem;
    }
  }

.btn {
  border: none;
  cursor: pointer;
  font-weight: 600;
  padding: 0.5rem;
  text-transform: uppercase;
}
  .btn.--primary {
    background: var(--greenPrimary);
    color: var(--black);
  }
    .btn.--primary:hover {
      background: var(--greenSecondary);
      color: var(--camel);
    }
</style>
