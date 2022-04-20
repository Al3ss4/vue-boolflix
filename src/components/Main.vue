<template>
  <main>
      <div class="container">
          <div>
              <div>
                  <Card v-for="film in films" :key="film.id" :features="film"/>
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
        inputRicerca: String,
    }
}
</script>