<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";
export default {
  components: {
    AppCard,
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
</template>

<style lang="scss" scoped></style>
