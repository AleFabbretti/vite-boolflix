<script>
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div>
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('search')">
      <input
        type="text"
        placeholder="Cerca il tuo film"
        v-model="store.searchText"
      />
      <button type="submit">Cerca</button>
      <button type="reset" @click="$emit('search', 'reset')">Reset</button>
    </form>
  </div>
</template>

<style lang="scss" scoped></style>
