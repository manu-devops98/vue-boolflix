<template>
  <header class="container-fluid">
    <Search @doInput="searchTitles($event)" />
  </header>
</template>

<script>
import Search from "./Search.vue";
export default {
  name: "Header",
  components: {
    Search,
  },
  data() {
    return {
      inputValue: "",
    };
  },
  methods: {
    searchTitles(text) {
      this.inputValue = text;
      this.$emit("doTitle", this.inputValue);
    },
  },
};
</script>

<style lang="scss">
header {
  height: 80px;
  background-color: black;
}
</style>
