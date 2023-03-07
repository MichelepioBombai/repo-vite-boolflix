<script>
export default {
  props: {
    title: String,
    OriginalTitle: String,
    lang: String,
    vote: Number,
    poster: String,
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

<style></style>
