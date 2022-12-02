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
  <div class="header pb-3">
    <div class="d-flex justify-content-center">
      <h1>BOOLFLIX</h1>
    </div>
    <form
      class="d-flex justify-content-center"
      @submit.prevent="$emit('search')"
    >
      <input
        class="border-0"
        type="text"
        placeholder="Cerca il tuo film"
        v-model="store.searchText"
      />
      <button class="mx-3" type="submit">Cerca</button>
      <button type="reset" @click="$emit('search', 'reset')">Reset</button>
    </form>
  </div>
</template>

<style lang="scss" scoped>
.header {
  background-color: rgba(0, 0, 0, 0.8);
}
h1 {
  color: #e50914;
  font-weight: bold;
  font-size: 50px;
}
button {
  background-color: #e50914;
  color: white;
  border: none;
  border-radius: 5px;
  width: 70px;
}
</style>
