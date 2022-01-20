<template>
  <div id="app">
    <Header @doTitle="search($event)" />
    <Main :films="films" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  data() {
    return {
      apiKey: "84e9c8b19a36589396bf63537bcc1640",
      queryApi: "https://api.themoviedb.org/3/search/",
      inputValue: "",
      language: "it-IT",
      films: null,
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    search(text) {
      this.inputValue = text;
      this.getFilms();
    },
    getFilms() {
      this.films = null;
      const endpoint = "movie";
      const parameters = {
        api_key: this.apiKey,
        language: this.language,
        query: this.inputValue,
      };
      axios
        .get(`${this.queryApi}${endpoint}`, {
          params: parameters,
        })
        .then((result) => {
          console.log(result);
          this.films = result.data.results;
          console.log(this.films);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
#app {
}
</style>
