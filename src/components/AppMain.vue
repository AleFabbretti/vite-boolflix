<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";
import AppCardTvSeries from "./AppCardTvSeries.vue";
export default {
  components: {
    AppCard,
    AppCardTvSeries,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <section>
    <h3 v-if="store.movies.length > 0">MOVIES</h3>
    <ul class="container">
      <AppCardTvSeries v-for="movie in store.movies" :info="movie" />
    </ul>
  </section>
  <section class="container series">
    <h3 v-if="store.series.length > 0">SERIES</h3>
    <ul class="container">
      <AppCardTvSeries v-for="serie in store.series" :info="serie" />
    </ul>
  </section>
</template>

<style lang="scss" scoped>
.container {
  max-width: max-content;
  list-style: none;
  color: white;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
section {
  background-color: rgba(0, 0, 0, 0.8);
}
h3 {
  color: white;
  display: flex;
  justify-content: center;
}
</style>
