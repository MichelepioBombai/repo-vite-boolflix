<script>
export default {
  props: {
    title: String,
    OriginalTitle: String,
    lang: String,
    vote: Number,
    poster: String,
    info: String,
  },

  methods: {
    getFlag(country) {
      country = country.toUpperCase();

      if (country == "EN") return "https://flagsapi.com/GB/flat/64.png";
      return "https://flagsapi.com/" + country + "/flat/64.png";
    },

    getImage(poster) {
      return "https://image.tmdb.org/t/p/w342" + poster;
    },
  },
};
</script>

<template>
  <div class="cardInfo col pt-4">
    <img :src="getImage(poster)" alt="" />
    <div class="details">
      <h3>
        Titolo:
        {{ title }}
      </h3>
      <p>Titolo originale: {{ OriginalTitle }}</p>
      <p>Paese:<img class="flag" :src="getFlag(lang)" /></p>
      <p>Voto: {{ vote }}</p>
      <p>Overview: {{ info }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.details {
  color: white;
  margin-top: 20px;
  width: 342px;
  background-color: black;
  height: 516px;
  overflow: auto;
}

img {
  height: 512px;
}
.flag {
  height: 100%;
}
</style>
