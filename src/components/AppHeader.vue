<script>
import axios from "axios";
import { store } from "../data/store";
import { series } from "../data/store";

export default {
  data() {
    return {
      store,
      series,
      searchQuery: "",
    };
  },

  methods: {
    searchMoviesAndSerieTv() {
      axios
        .all([
          axios.get("https://api.themoviedb.org/3/search/movie", {
            params: {
              api_key: "59e2418b4425b86d44b365d940853ff8",
              query: this.searchQuery,
            },
          }),
          axios.get("https://api.themoviedb.org/3/search/tv", {
            params: {
              api_key: "59e2418b4425b86d44b365d940853ff8",
              query: this.searchQuery,
            },
          }),
        ])
        .then(
          axios.spread((moviesResponse, serieTvResponse) => {
            store.movies = moviesResponse.data.results;
            series.serieTv = serieTvResponse.data.results;
          })
        );
    },
  },
};
</script>

<template>
  <h1>Movie Search App</h1>
  <form @submit.prevent="searchMoviesAndSerieTv">
    <label for="searchInput">Search for a movie/serie-tv:</label>
    <input type="text" id="searchInput" v-model="searchQuery" />
    <button type="submit">Search</button>
  </form>
</template>
<style lang="scss" scoped></style>
