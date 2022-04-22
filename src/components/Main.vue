<template>
  <main>
      <div class="container">
          <div>
              <div>
                  <Card v-for="film in films" :key="film.id" :features="film" :img="film.poster_path" :vote="film.vote_average"/>
              </div>
              <div>
                  <Card v-for="serie in series" :key="serie.id" :features="serie" :img="serie.poster_path" :vote="serie.vote_average"/>
              </div>
          </div>
      </div>
  </main>
</template>
<script>


import Card from './Card.vue';

export default {
    name: 'MainComp',
    components : {
        Card ,
    },
    props : {
        films: Array,
        series: Array,
        inputRicerca: String,

    }
}
</script>

<style lang="scss" scoped>


</style>