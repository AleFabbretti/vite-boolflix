<script>
import axios from "axios";
import { store } from "./store.js";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    searchMovie(data = "") {
      if (data === "reset") {
        this.store.searchText = "";
      }
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "8fcf7b9bc08c090a4dda3f181c9cc521",
            query: this.store.searchText,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.store.movies = resp.data.results;
        })
        .catch((err) => {
          this.store.movies = [];
          this.store.series = [];
        });
      if (data === "reset") {
        this.store.searchText = "";
      }
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "25f24fd3ebdb2b8fa4786f77d8241b8d",
            query: this.store.searchText,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.store.series = resp.data.results;
        })
        .catch((err) => {
          this.store.movies = [];
          this.store.series = [];
        });
    },
  },
};
</script>

<template>
  <div class="body">
    <AppHeader @search="searchMovie" />
    <AppMain />
  </div>
</template>

<style lang="scss">
.body {
  background-image: url(./assets/IT-it-20221128-popsignuptwoweeks-perspective_alpha_website_large.jpg);
  height: 100vh;
}
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");
@import "./style/global.scss";
</style>
