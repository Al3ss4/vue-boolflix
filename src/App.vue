<template>
  <div id="app">
    <Header @ricerca='ricercaFilm'/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      key: "e73169f9140d1ed90b3e169c4bd87464",
      language: "it-IT",
      arrayMovies: [],
    };
  },
  methods: {
    ricercaFilm(text) {
      axios
        .get(this.apiURL, {
          params: {
            apiKey: this.key,
            language: this.language,
            query: text,
          },
        })
        .then((response) => {
          this.arrayMovies = response.data.results;
        });
      console.log(text);
    }
  },
};
</script>

<style lang="scss">
@import "@/style/commons.scss";
</style>

<!-- Milestone 1:
Creare un layout base con una searchbar (una input e un button) in cui possiamo
scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il
bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.
Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni
film trovato:
1. Titolo
2. Titolo Originale
3. Lingua
4. Voto -->