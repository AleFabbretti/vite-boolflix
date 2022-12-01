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
  <section class="container">
    <ul>
      <AppCard v-for="movie in store.movies" :info="movie" />
    </ul>
  </section>
  <section class="container series">
    <ul>
      <AppCardTvSeries v-for="serie in store.series" :info="serie" />
    </ul>
  </section>
</template>

<style lang="scss" scoped>
.container {
  background-color: black;
  max-width: max-content;
  & ul {
    list-style: none;
    color: white;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>
