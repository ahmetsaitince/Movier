<template>
  <div class="container-sm mt-5">
    <h1>Movier</h1>
    <Search @make-search="newSearch" />
    <div class="results row mx-auto justify-content-center text-dark">
      <Catalogue :movies="movies" />
    </div>
  </div>
</template>

<script>
import Search from './components/Search.vue';
import Catalogue from './components/Catalogue.vue';

export default {
  name: 'App',
  components: {
    Search,
    Catalogue,
  },
  data() {
    return {
      movies: [],
      search_key: '',
    };
  },
  methods: {
    async newSearch(newSearch) {
      this.search_key = newSearch.key;
      await this.fetchTasks(); // Call fetchTasks when newSearch is triggered
    },
    async fetchTasks() {
      try {
        const res = await fetch(
          `https://www.omdbapi.com/?s=${this.search_key}&apikey=3ff5ca2b`
        );

        if (!res.ok) {
          throw new Error('Failed to fetch data');
        }
        const data = await res.json();

        // Extract relevant information from the API response
        const movieDetails = data.Search;

        // Update the movies data property
        this.movies = movieDetails;
        console.log(this.movies);
      } catch (error) {
        console.log('Error fetching data: ', error);
      }
    },
  },
  async created() {
    await this.fetchTasks();
  },
};
</script>
