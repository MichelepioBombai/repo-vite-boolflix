<script>
import MovieData from "./MovieData.vue";
import TvSerieData from "./TvSerieData.vue";

export default {
  components: { MovieData, TvSerieData },
  props: {
    title: String,
    OriginalTitle: String,
    lang: String,
    vote: String,
  },
};
</script>
!
<template>
  <ul>
    <h2>Results:</h2>
    <li>
      <div class="infoMovies">
        <h3>{{ title }}</h3>
        <p>{{ OriginalTitle }}</p>
        <p>{{ lang }}</p>
        <p>{{ vote }}</p>
      </div>
    </li>
  </ul>

  <MovieData />
  <TvSerieData />
</template>

<style></style>
