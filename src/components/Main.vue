<template>
  <main>
    <div class="container-fluid d-flex flex-wrap">
      <div v-for="(film, index) in films" :key="index" class="box p-3">
        <h2>Titolo:</h2>
        <p>{{ film.title }}</p>
        <h2>Titolo Originale:</h2>
        <p>{{ film.original_title }}</p>
        <h2>Lingua:</h2>
        <i
          :class="
            film.original_language == 'en'
              ? 'flag flag-us'
              : `flag flag-${film.original_language}`
          "
        ></i>
        <h2>Voto:</h2>
        <p>{{ film.vote_average }}</p>
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
  props: ["films"],
};
</script>

<style lang="scss">
@import "~mdb-ui-kit/css/mdb.min.css";
.box {
  border: 2px solid black;
  width: calc(100% / 4);
}
</style>
