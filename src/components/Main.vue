<template>
  <main class="container">
    <div class="row">
      <div class="d-flex flex-wrap col-12 justify-content-center">
        <Card
          v-for="film in films"
          :key="film.id"
          :features="film"
          :img="film.poster_path"
          :vote="film.vote_average"
        />
      </div>
      <div class="d-flex flex-wrap col-12 justify-content-center">
        <Card
          v-for="serie in series"
          :key="serie.id"
          :features="serie"
          :img="serie.poster_path"
          :vote="serie.vote_average"
        />
      </div>
    </div>
  </main>
</template>
<script>
import Card from "./Card.vue";

export default {
  name: "MainComp",
  components: {
    Card,
  },
  props: {
    films: Array,
    series: Array,
    inputRicerca: String,
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: grey;
  color: black;
}
</style>