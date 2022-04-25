<template>
  <main class="container">
    <div class="row">
        <h1 class="text-center my-4">FILM</h1>
      <div class="d-flex flex-wrap justify-content-center mb-5">
          
        <Card
          v-for="film in films"
          :key="film.id"
          :features="film"
          :img="film.poster_path"
          :vote="film.vote_average"
        />
      </div>
        <h1 class="text-center m-4">TELEFILM</h1>
      <div class="d-flex flex-wrap  justify-content-center mt-5">
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
  overflow-y:scroll;
  overflow-x: hidden;
  .row{
    height: calc(100vh - 90px);
  }
}
</style>