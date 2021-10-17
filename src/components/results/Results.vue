<template>
  <b-row class="mt-4">
    <b-col>
      <b-card bg-variant="dark" text-variant="white" class="main-card">
        <h4 v-if="search.length === 0" class="text-center">
          Start by typing a word in search
        </h4>

        <h4 v-else-if="error" class="text-center">{{ error }}</h4>

        <div v-else-if="result">
          <h4>{{ title }}</h4>

          <Pronounciation :audio="audio" />

          <Meanings :result="result" />
        </div>
      </b-card> </b-col
  ></b-row>
</template>

<script>
import Pronounciation from "./Pronounciation.vue";
import Meanings from "./Meanings.vue";

export default {
  props: ["search", "result", "error"],
  computed: {
    title() {
      return this.result ? this.search : "";
    },
    audio() {
      let audio = null;

      let result = this.result;

      if (
        result &&
        "phonetics" in result[0] &&
        result[0].phonetics.length > 0 &&
        "audio" in result[0].phonetics[0]
      ) {
        audio = result[0].phonetics[0].audio;
      }
      return audio;
    },
  },
  components: {
    Pronounciation,
    Meanings,
  },
};
</script>

<style scoped>
.main-card {
  border: 5px solid #696969;
}
</style>
