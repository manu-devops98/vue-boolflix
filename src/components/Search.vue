<template>
  <div class="input-container">
    <label for="exampleFormControlInput1" class="form-label"
      >Cerca titoli</label
    >
    <input
      v-model="inputValue"
      type="text"
      class="form-control"
      id="exampleFormControlInput1"
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
.input-container {
  .form-control {
    width: 20%;
    padding: 0;
  }
}
</style>
