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
              overview: movie.overview,
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
              overview: serie.overview,
            };
          });
          store.serieTv = serieTv;
        });
    },
  },
};
</script>

<template>
  <nav class="navbar bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand text-white d-flex"
        ><img
          src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png"
          alt=""
      /></a>
      <ul>
        <li class="text-white">Home</li>
        <li>Serie TV</li>
        <li>Film</li>
        <li>Originali</li>
        <li>Aggiunti di recente</li>
        <li>La mia lista</li>
      </ul>

      <div>
        <form
          class="d-flex"
          role="search"
          @submit.prevent="searchMoviesAndSerieTv"
        >
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
            v-model="searchQuery"
          />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>
<style lang="scss" scoped>
img {
  width: 150px;
}
.navbar {
  position: relative;
}

ul {
  li {
    list-style: none;
    color: gray;
    font-size: 20px;
    cursor: pointer;
  }
  display: flex;
  gap: 40px;
  position: absolute;
  left: 210px;
  top: 15px;
}
</style>
