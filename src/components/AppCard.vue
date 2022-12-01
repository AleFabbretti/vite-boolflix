<script>
import CountryFlag from "vue-country-flag-next";
export default {
  props: {
    info: Object,
  },
  components: {
    CountryFlag,
  },
  methods: {
    getFlag(lang) {
      if (lang == "en") {
        return "gb";
      }
      return lang;
    },
  },
  computed: {
    vote() {
      return Math.ceil(this.info.vote_average / 2);
    },
  },
};
</script>

<template>
  <li>
    <div class="my-card m-2">
      <img
        :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`"
        :alt="info.title"
      />

      <h4>Titolo: {{ info.title }}</h4>
      <h6>Titolo originale: {{ info.original_title }}</h6>
      <h6>
        Lingua originale:
        <country-flag
          :country="getFlag(info.original_language)"
          size="medium"
        />
      </h6>
      <h6 v-if="vote >= 1">
        <font-awesome-icon v-for="n in vote" icon="fa-solid fa-star" />
        <font-awesome-icon v-for="n in 5 - vote" icon="fa-regular fa-star" />
        Voto: {{ vote }}
      </h6>
    </div>
  </li>
</template>

<style lang="scss" scoped>
.my-card {
  width: 342px;
  height: 700px;
  border: 1px solid white;
}
</style>
