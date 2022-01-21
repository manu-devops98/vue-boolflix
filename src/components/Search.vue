<template>
  <div class="container-fluid d-flex justify-content-between">
    <input
      v-model="inputValue"
      type="text"
      class="form-control"
      id="exampleFormControlInput1"
      placeholder="Cerca.."
    />
    <button
      @click="$emit('doInput', inputValue)"
      type="button"
      class="btn btn-danger"
    >
      Cerca
    </button>
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
  .form-control {
    width: 100%;
    padding: 10px;
    margin-right: 20px;
  }
}
</style>
