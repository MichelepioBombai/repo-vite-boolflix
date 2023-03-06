<script>
import MovieData from "./MovieData.vue";
import TvSerieData from "./TvSerieData.vue";
import { store } from "../data/store";

export default {
  data() {
    return {
      store,
    };
  },
  components: { MovieData, TvSerieData },
};
</script>
!
<template>
  <div>
    <div>
      <h2>Results:</h2>
      <MovieData
        v-for="movie in store.movies"
        :key="movie.id"
        :title="movie.title"
        :OriginalTitle="movie.original_title"
        :lang="movie.original_language"
        :vote="movie.vote_average"
      />
    </div>
  </div>

  <MovieData />
  <TvSerieData />
</template>

<style></style>
