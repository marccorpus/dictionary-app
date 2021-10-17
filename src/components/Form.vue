<template>
  <b-row class="mt-4">
    <b-col md="6">
      <b-form-group label="Search a Word">
        <b-form-input
          class="text-light shadow-none border-bottom input"
          v-model.trim="search"
          @input="searchChangeHandler"
        ></b-form-input>
      </b-form-group>
    </b-col>
  </b-row>
</template>

<script>
export default {
  emits: ["search-change"],
  data() {
    return {
      search: "",
    };
  },
  methods: {
    searchChangeHandler() {
      this.$emit("search-change", this.search);
    },
  },
};
</script>

<style scoped>
.input,
.input:focus {
  background: none;
  border: none;
  border-radius: 0px;
}
</style>
