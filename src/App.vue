<template>
  <div id="app">
    <b-container>
      <Header :title="title" />
      <Form @search-change="searchChangeHandler" />
      <Results :search="search" :result="result" :error="error" />
    </b-container>
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Results from "./components/results/Results.vue";

export default {
  data() {
    return {
      timer: null,
      search: "",
      result: null,
      error: null,
    };
  },
  computed: {
    title() {
      return this.search || "WORD HUNT";
    },
  },
  watch: {
    search(value) {
      if (value) {
        clearTimeout(this.timer);

        this.result = null;
        this.error = null;

        this.timer = setTimeout(() => {
          axios
            .get(`https://api.dictionaryapi.dev/api/v2/entries/en/${value}`)
            .then((response) => {
              this.result = response.data;
              this.error = null;
            })
            .catch(() => {
              this.result = null;
              this.error = "Word not found.";
            });
        }, 500);
      }
    },
  },
  methods: {
    searchChangeHandler(search) {
      this.search = search;
    },
  },
  components: {
    Header,
    Form,
    Results,
  },
};
</script>

<style>
body {
  background-color: rgb(40, 44, 52) !important;
}
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  margin: 60px 0 30px 0;
}
</style>
