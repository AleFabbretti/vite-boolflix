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
        class="poster"
        :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`"
        :alt="info.name"
      />
      <div class="info py-4 px-3">
        <h4>Titolo: {{ info.title || info.name }}</h4>
        <h6>
          Titolo originale: {{ info.original_title || info.original_name }}
        </h6>
        <h6>
          Lingua originale:
          <country-flag
            :country="getFlag(info.original_language)"
            size="medium"
          />
        </h6>
        <h6 v-if="vote >= 1">
          Voto: {{ vote }}
          <font-awesome-icon
            class="color"
            v-for="n in vote"
            icon="fa-solid fa-star"
          />
          <font-awesome-icon v-for="n in 5 - vote" icon="fa-regular fa-star" />
        </h6>
      </div>
    </div>
  </li>
</template>

<style lang="scss" scoped>
.my-card {
  width: 342px;
  position: relative;
  & img {
    height: 450px;
    object-fit: cover;
    object-position: top;
    width: 100%;
  }
}
.color {
  color: #e50914;
}

.info {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  transition: 0.5s ease;
  background-color: black;
  opacity: 0;
}
.my-card:hover .info {
  cursor: pointer;
  opacity: 1;
}
</style>
