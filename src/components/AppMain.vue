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
    <h2>Results:</h2>
    <div>
      <MovieData
        v-for="movie in store.movies"
        :key="movie.id"
        :title="movie.title"
        :OriginalTitle="movie.original_title"
        :lang="movie.original_language"
        :vote="movie.vote_average"
      />
    </div>
    <div>
      <TvSerieData
        v-for="serie in store.seriesTv"
        :key="serie.id"
        :title="serie.name"
        :OriginalTitle="serie.original_name"
        :lang="serie.original_language"
        :vote="serie.vote_average"
      />
    </div>
  </div>

  <MovieData />
  <TvSerieData />
</template>

<style></style>
