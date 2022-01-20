<template>
  <main>
    <div class="container-fluid d-flex">
      <div class="container-film w-100">
        <!-- ciclo v-for su film  -->
        <div
          v-for="(film, index) in films"
          :key="index + film.id"
          class="box p-3"
        >
          <img
            :src="
              film.poster_path == null
                ? `${defaultImage}`
                : `${imageUrl}${sizeImage}${film.poster_path}`
            "
            :alt="film.title"
          />
          <h2>Titolo Film:</h2>
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
          <p>{{ numbInteger(film.vote_average) }}</p>
          <font-awesome-icon icon="star" />
        </div>
      </div>
      <div class="container-serie w-100">
        <!-- ciclo v-for su serie  -->
        <div
          v-for="(serie, index) in series"
          :key="index + serie.id"
          class="box p-3"
        >
          <img
            :src="
              serie.poster_path == null
                ? `${defaultImage}`
                : `${imageUrl}${sizeImage}${serie.poster_path}`
            "
            :alt="serie.name"
          />
          <h2>Titolo Serie:</h2>
          <p>{{ serie.name }}</p>
          <h2>Titolo Originale:</h2>
          <p>{{ serie.original_name }}</p>
          <h2>Lingua:</h2>
          <i
            :class="
              serie.original_language == 'en'
                ? 'flag flag-us'
                : `flag flag-${serie.original_language}`
            "
          ></i>
          <h2>Voto:</h2>
          <!-- <p>{{ serie.vote_average }}</p> -->
          <p>{{ numbInteger(serie.vote_average) }}</p>
          <font-awesome-icon icon="star" class="active" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
// import { library } from "@fortawesome/fontawesome-svg-core";
// import { faUserSecret } from "@fortawesome/free-solid-svg-icons";
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

// library.add(faUserSecret);

export default {
  name: "Main",
  components: {
    // FontAwesomeIcon,
  },
  data() {
    return {
      sizeImage: "w342",
      imageUrl: "https://image.tmdb.org/t/p/",
      defaultImage: "https://picsum.photos/350/500",
    };
  },
  props: ["films", "series"],
  methods: {
    numbInteger(number) {
      return Math.round(number / 2);
    },
  },
};
</script>

<style lang="scss">
@import "~mdb-ui-kit/css/mdb.min.css";
// @import "@fortawesome/fontawesome-free";
main {
  background-color: black;
  .container-film,
  .container-serie {
    .box {
      border: 2px solid black;
      // width: calc(100% / 4);
      width: 100%;
      background-color: black;
      color: white;
      .fa-star {
        color: #ffbd02;
        color: white;
        font-size: 2em;
        &.active {
          color: #ffbd02;
        }
      }
    }
  }
}
</style>
