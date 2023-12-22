<template>
  <div
    :key="movie.imdbID"
    v-for="movie in movies"
    class="col-3 w-25 rounded bg-light m-2"
  >
    <Movie :movie="movie" />
  </div>
</template>

<script>
import Movie from './Movie';

export default {
  name: 'Catalogue',
  components: {
    Movie,
  },
  props: {
    movies: Array,
  },
};
</script>

<style scope></style>
