<template>
  <div class="container d-flex justify-content-between">
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
.container {
  .form-control {
    width: 70%;
    padding: 10px;
  }
}
</style>
