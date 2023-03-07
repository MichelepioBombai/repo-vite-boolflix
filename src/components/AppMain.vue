<script>
import cardData from "./cardData.vue";

import { store } from "../data/store";

export default {
  data() {
    return {
      store,
    };
  },
  components: { cardData },
};
</script>
!
<template>
  <div>
    <div>
      <h2>Films:</h2>
      <cardData
        v-for="movie in store.movies"
        :key="movie.id"
        :title="movie.title"
        :OriginalTitle="movie.OriginalTitle"
        :lang="movie.lang"
        :vote="movie.vote"
        :poster="movie.poster"
      />
    </div>
    <div>
      <h2>Serie-Tv:</h2>
      <cardData
        v-for="serie in store.serieTv"
        :key="serie.id"
        :title="serie.title"
        :OriginalTitle="serie.OriginalTitle"
        :lang="serie.lang"
        :vote="serie.vote"
        :poster="serie.poster"
      />
    </div>
  </div>

  <!-- <MovieData />
  <TvSerieData /> -->
</template>

<style></style>
