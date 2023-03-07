<script>
import axios from "axios";
import { store } from "../data/store";

export default {
  data() {
    return {
      searchQuery: "",
    };
  },

  methods: {
    searchMoviesAndSerieTv() {
      this.searchMovies();
      this.searchSerieTv();
    },

    searchMovies() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "59e2418b4425b86d44b365d940853ff8",
            query: this.searchQuery,
          },
        })
        .then((response) => {
          const movies = response.data.results.map((movie) => {
            return {
              title: movie.title,
              OriginalTitle: movie.original_title,
              lang: movie.original_language,
              vote: movie.vote_average,
              poster: movie.poster_path,
            };
          });

          console.log(store.movies);
          store.movies = movies;
        });
    },

    searchSerieTv() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "59e2418b4425b86d44b365d940853ff8",
            query: this.searchQuery,
          },
        })
        .then((response) => {
          const serieTv = response.data.results.map((serie) => {
            return {
              title: serie.name,
              OriginalTitle: serie.original_name,
              lang: serie.original_language,
              vote: serie.vote_average,
              poster: serie.poster_path,
            };
          });
          store.serieTv = serieTv;
        });
    },
  },
};
</script>

<template>
  <h1>Boolflix</h1>
  <form @submit.prevent="searchMoviesAndSerieTv">
    <label for="searchInput">Search for a movie/serie-tv:</label>
    <input type="text" id="searchInput" v-model="searchQuery" />
    <button type="submit">Search</button>
  </form>
</template>
<style lang="scss" scoped></style>
