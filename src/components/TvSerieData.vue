<script>
export default {
  props: {
    title: String,
    OriginalTitle: String,
    lang: String,
    vote: String,
  },
};
</script>

<template>
  <ul>
    <li>
      <div class="infoSerietv">
        <h3>{{ title }}</h3>
        <p>{{ OriginalTitle }}</p>
        <p>{{ lang }}</p>
        <p>{{ vote }}</p>
      </div>
    </li>
  </ul>
</template>

<style lang="scss" scoped></style>
