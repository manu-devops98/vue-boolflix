<template>
  <main>
    <div class="container-title">
      <ul>
        <li v-for="(title, index) in titles" :key="index">
          <h1>{{ title.title }}</h1>
          <h1>{{ title.original_title }}</h1>
          <h1>{{ title.original_language }}</h1>
          <h1>{{ title.vote_average }}</h1>
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  components: {},
  data() {
    return {
      apiKey: "84e9c8b19a36589396bf63537bcc1640",
      queryApi: "https://api.themoviedb.org/3/search/movie",
      titles: null,
      textInput: "",
    };
  },
  props: {
    value: {
      type: String,
    },
  },
  methods: {
    searchInput() {
      if (this.value == "") {
        return this.textInput;
      } else {
        return (this.textInput = this.value);
      }
    },
    getTitles() {
      this.titles = null;
      axios
        .get(this.queryApi, {
          params: {
            apy_key: this.apiKey,
            query: this.textInput,
          },
        })
        .then((result) => {
          console.log(result);
          this.titles = result.data.results;
          console.log(this.titles);
          console.log(this.queryApi);
          console.log("valueee", this.value);
          this.$emit("apiCall", this.titles);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  created() {
    this.searchInput();
  },
  mounted() {
    this.getTitles();
  },
};
</script>

<style lang="scss"></style>
