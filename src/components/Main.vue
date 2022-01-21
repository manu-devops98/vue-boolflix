<template>
  <main class="mt-5">
    <div v-if="films" class="container">
      <div class="row row-cols-6">
        <div v-if="films" class="col-12">
          <h1 class="text-white mb-4">Film</h1>
          <div class="container-film d-flex">
            <!-- ciclo v-for su film  -->
            <div
              v-for="(film, index) in films"
              :key="index + film.id"
              class="box"
            >
              <img
                :src="
                  film.poster_path == null
                    ? `${defaultImage}`
                    : `${imageUrl}${sizeImage}${film.poster_path}`
                "
                :alt="film.title"
                class="w-100 mb-4"
              />
              <div class="info-movies">
                <ul class="list-unstyled">
                  <li>
                    <p class="fw-bold">
                      Titolo film:
                      <span class="fw-normal">{{ film.title }}</span>
                    </p>
                  </li>
                  <li>
                    <p
                      :class="
                        film.title == film.original_title ? 'd-none' : 'fw-bold'
                      "
                    >
                      Titolo originale:
                      <span class="fw-normal">{{ film.original_title }}</span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Lingua:
                      <span
                        ><i
                          :class="
                            film.original_language == 'en'
                              ? 'flag flag-us'
                              : `flag flag-${film.original_language}`
                          "
                        ></i
                      ></span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Voto:
                      <span
                        ><font-awesome-icon
                          icon="star"
                          v-for="(star, index) in 5"
                          :key="index"
                          :class="
                            starActive(numbInteger(film.vote_average), index)
                          "
                      /></span>
                    </p>
                  </li>
                  <li>
                    <div v-if="film.overview" class="overview">
                      <p v-if="film.overview" class="fw-bold">
                        Riassunto: <span>{{ film.overview }}</span>
                      </p>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <!-- SERIE TV  -->
        <div v-if="series" class="col-12">
          <h1 class="text-white mb-4">Serie TV</h1>
          <div class="container-serie d-flex">
            <!-- ciclo v-for su serie  -->
            <div v-for="(serie, index) in series" :key="index" class="box">
              <img
                :src="
                  serie.poster_path == null
                    ? `${defaultImage}`
                    : `${imageUrl}${sizeImage}${serie.poster_path}`
                "
                :alt="serie.name"
                class="w-100 mb-4"
              />
              <div class="info-movies">
                <ul class="list-unstyled">
                  <li>
                    <p class="fw-bold">
                      Titolo film:
                      <span class="fw-normal">{{ serie.name }}</span>
                    </p>
                  </li>
                  <li>
                    <p
                      :class="
                        serie.name == serie.original_name ? 'd-none' : 'fw-bold'
                      "
                    >
                      Titolo originale:
                      <span class="fw-normal">{{ serie.original_name }}</span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Lingua:
                      <span
                        ><i
                          :class="
                            serie.original_language == 'en'
                              ? 'flag flag-us'
                              : `flag flag-${serie.original_language}`
                          "
                        ></i
                      ></span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Voto:
                      <span
                        ><font-awesome-icon
                          icon="star"
                          v-for="(star, index) in 5"
                          :key="index"
                          :class="
                            starActive(numbInteger(serie.vote_average), index)
                          "
                      /></span>
                    </p>
                  </li>
                  <li>
                    <div v-if="serie.overview" class="overview">
                      <p class="fw-bold">
                        Riassunto: <span>{{ serie.overview }}</span>
                      </p>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- default films  -->
    <div v-else class="container">
      <div class="row row-cols-6">
        <div class="col-12">
          <h1 class="text-white mb-4">Film</h1>
          <div class="container-film d-flex">
            <!-- ciclo v-for su film di default  -->
            <div
              v-for="(defaults, index) in defaultFilms"
              :key="index"
              class="box"
            >
              <img
                :src="
                  defaults.poster_path == null
                    ? `${defaultsImage}`
                    : `${imageUrl}${sizeImage}${defaults.poster_path}`
                "
                :alt="defaults.title"
                class="w-100 mb-4"
              />
              <div class="info-movies">
                <ul class="list-unstyled">
                  <li>
                    <p class="fw-bold">
                      Titolo Film:
                      <span class="fw-normal">{{ defaults.title }}</span>
                    </p>
                  </li>
                  <li>
                    <p
                      :class="
                        defaults.title == defaults.original_title
                          ? 'd-none'
                          : 'fw-bold'
                      "
                    >
                      Titolo originale:
                      <span class="fw-normal">{{
                        defaults.original_title
                      }}</span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Lingua:
                      <span
                        ><i
                          :class="
                            defaults.original_language == 'en'
                              ? 'flag flag-us'
                              : `flag flag-${defaults.original_language}`
                          "
                        ></i
                      ></span>
                    </p>
                  </li>
                  <li>
                    <p class="fw-bold">
                      Voto:
                      <span
                        ><font-awesome-icon
                          icon="star"
                          v-for="(star, index) in 5"
                          :key="index"
                          :class="
                            starActive(
                              numbInteger(defaults.vote_average),
                              index
                            )
                          "
                      /></span>
                    </p>
                  </li>
                  <li>
                    <div v-if="defaults.overview" class="overview">
                      <p class="fw-bold">
                        Riassunto: <span>{{ defaults.overview }}</span>
                      </p>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
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
      sizeImage: "w342",
      imageUrl: "https://image.tmdb.org/t/p/",
      defaultImage: "https://picsum.photos/350/500",
      defaultFilms: [],
      defaultApi:
        "https://api.themoviedb.org/3/search/movie?api_key=84e9c8b19a36589396bf63537bcc1640&query=marvel",
    };
  },
  props: ["films", "series"],
  mounted() {
    this.defaultValueFilms();
  },
  methods: {
    numbInteger(number) {
      return Math.round(number / 2);
    },
    starActive(number, index) {
      while (number > index) {
        return "active";
      }
    },
    defaultValueFilms() {
      this.defaultFilms = [];
      axios
        .get(this.defaultApi)
        .then((result) => {
          console.log(result);
          this.defaultFilms = result.data.results;
          console.log(this.defaultFilms);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "~mdb-ui-kit/css/mdb.min.css";
main {
  background-color: black;
  .container {
    width: 95%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    .container-film,
    .container-serie {
      display: flex;
      flex-wrap: wrap;
      margin: 10px;
      .box {
        margin: 0.4em;
        background-color: black;
        color: white;
        width: calc(100% / 6 - 0.8em);
        position: relative;
        &:hover {
          .info-movies {
            display: block;
            transform: scale(1.2);
            z-index: 10;
          }
        }
        .info-movies {
          display: none;
          padding: 0.5em;
          border: 1px solid white;
          width: 100%;
          height: 100%;
          position: absolute;
          top: 0;
          left: 0;
          background-color: black;
          overflow-y: auto;
          li {
            margin-bottom: 0;
            .overview {
              overflow-y: scroll;
              height: 150px;
            }
            p {
              font-size: 1em;
            }
            span {
              font-size: 0.8em;
            }
          }
        }
        .fa-star {
          color: white;
          font-size: 1.4em;
          &.active {
            color: #ffbd02;
          }
        }
      }
    }
  }
}
</style>
