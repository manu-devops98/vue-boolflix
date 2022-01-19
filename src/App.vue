<template>
  <div id="app">
    <Header @doTitle="doSearch($event)" />
    <Main :value="inputValue" />
    <!-- @apiCall="printTitle($event)" -->
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  data() {
    return {
      inputValue: "",
      titles: [],
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    doSearch(value) {
      this.inputValue = value;
      console.log(this.inputValue);
    },
    // printTitle(array) {
    //   this.titles = array;
    //   console.log(this.titles);
    // },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
#app {
}
</style>
