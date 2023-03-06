<script>
export default {};
</script>

<template>
  <div>
    <div>
      <AppMain
        v-for="movie in movies"
        :key="movie.id"
        :title="movie.title"
        :OriginalTitle="movie.original_title"
        :lang="movie.original_language"
        :vote="movie.vote_average"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
