<template>
  <div class="container-fluid d-flex justify-content-between p-3">
    <div class="container-logo">
      <img class="" src="../assets/logo.png" alt="" />
    </div>
    <div class="text-search d-flex justify-content-end">
      <input
        v-model="inputValue"
        type="text"
        class="form-control"
        id="exampleFormControlInput1"
        placeholder="Cerca.."
        @keyup.enter="$emit('enterInput', inputValue)"
      />
      <button
        @click="$emit('doInput', inputValue)"
        type="button"
        class="btn btn-danger"
      >
        Cerca
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      inputValue: "",
    };
  },
};
</script>

<style lang="scss">
.container-fluid {
  .container-logo {
    width: 50%;
    img {
      width: 30%;
    }
  }
  .text-search {
    width: 50%;
    height: 50%;
    .form-control {
      width: 80%;
      padding: 10px;
      margin-right: 20px;
    }
  }
}
</style>
