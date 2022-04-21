<template>
  <div id="app">
    <Header @ricerca="ricercaFilm" />
    <Main
      :films="arrayMovies"
      :series="arraySeries"
      :inputSearch="searchText"
    />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiTvUrl: "https://api.themoviedb.org/3/search/tv",
      key: "e73169f9140d1ed90b3e169c4bd87464",
      language: "it-IT",
      arrayMovies: [],
      arraySeries: [],
      searchText: "",
    };
  },
  methods: {
    ricercaFilm(text) {
      this.searchText = text;

      const request = {
        params: {
          api_key: this.key,
          language: this.language,
          query: text,
        },
      };
      const movies = axios.get(this.apiURL, request);
      const series = axios.get(this.apiTvUrl, request);
      debugger;

      axios
        .all([movies, series])
        .then(
          axios.spread((moviesArray, tvArray) => {
            this.arrayMovies = moviesArray.data.results;
            this.arraySeries = tvArray.data.results;
            console.log(tvArray.data.results, moviesArray.data.results);
          })
        )
        .catch((errors) => {
          // react on errors.
          console.error(errors);
        });
    },
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

<!-- Milestone 2:
Trasformiamo la stringa statica della lingua in una vera e propria bandiera della
nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della
nazione ritornata dall’API (le flag non ci sono in FontAwesome).
Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca
dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando
attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di
risposta diversi, simili ma non sempre identici)-->