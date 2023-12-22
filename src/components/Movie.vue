<template>
  <div class="thumbnail position-relative">
    <img :src="movie.Poster" :alt="movie.Title" class="img-fluid mb-2" />
    <div class="btn btn-danger position-absolute end-0 me-1 mt-1">
      {{ movie.Type }}
    </div>
  </div>
  <div>
    <h4 class="mb-0">{{ movie.Title }}</h4>
    <p>{{ movie.Year }}</p>
  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
    movie: Object,
  },
};
</script>

<style scope>
.btn {
  cursor: auto !important;
}
</style>
