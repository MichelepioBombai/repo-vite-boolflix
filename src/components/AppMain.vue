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
  <div class="container">
    <div v-if="store.movies.length">
      <h2 class="mb-3 mt-3 text-white">Movies:</h2>
      <div class="row row-cols-3">
        <cardData
          v-for="movie in store.movies"
          :key="movie.id"
          :title="movie.title"
          :OriginalTitle="movie.OriginalTitle"
          :lang="movie.lang"
          :vote="movie.vote"
          :poster="movie.poster"
          :info="movie.overview"
        />
      </div>
    </div>
    <div v-if="store.serieTv.length">
      <h2 class="mb-3 mt-5 text-white">Serie-TV:</h2>
      <div class="row row-cols-3">
        <cardData
          v-for="serie in store.serieTv"
          :key="serie.id"
          :title="serie.title"
          :OriginalTitle="serie.OriginalTitle"
          :lang="serie.lang"
          :vote="serie.vote"
          :poster="serie.poster"
          :info="serie.overview"
        />
      </div>
    </div>
    <h2 class="mt-5 text-white" v-else>inizia la ricerca...</h2>
  </div>
</template>

<style lang="scss" scoped></style>
