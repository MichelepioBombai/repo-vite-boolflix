<script>
export default {
  props: {
    title: String,
    OriginalTitle: String,
    lang: String,
    vote: Number,
  },

  methods: {
    getFlag(country) {
      country = country.toUpperCase();

      if (country == "EN") return "https://flagsapi.com/GB/flat/64.png";
      return "https://flagsapi.com/" + country + "/flat/64.png";
    },
  },
};
</script>

<template>
  <ul>
    <li>
      <div class="infoMovies">
        <h3>{{ title }}</h3>
        <p>{{ OriginalTitle }}</p>
        <p><img :src="getFlag(lang)" /></p>
        <p>{{ vote }}</p>
      </div>
    </li>
  </ul>
</template>

<style lang="scss" scoped></style>
