<template>
  <div id="app">
    <Header @doTitle="getTitles($event)" />
    <Main :titles="titles" />
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
      queryApi:
        "https://api.themoviedb.org/3/search/movie?api_key=84e9c8b19a36589396bf63537bcc1640&query=",
      titles: null,
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    getTitles(value) {
      this.titles = null;
      axios
        .get(this.queryApi + value)
        .then((result) => {
          console.log(result);
          this.titles = result.data.results;
          console.log(this.titles);
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
