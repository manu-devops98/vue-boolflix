<template>
  <main>
    <div class="container-fluid d-flex flex-wrap">
      <div v-for="(title, index) in titles" :key="index" class="box p-3">
        <h2>Titolo:</h2>
        <p>{{ title.title }}</p>
        <h2>Titolo Originale:</h2>
        <p>{{ title.original_title }}</p>
        <h2>Lingua:</h2>
        <p>{{ title.original_language }}</p>
        <h2>Voto:</h2>
        <p>{{ title.vote_average }}</p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  components: {},
  data() {
    return {};
  },
  props: ["titles"],
};
</script>

<style lang="scss">
.box {
  border: 2px solid black;
  width: calc(100% / 4);
}
</style>
