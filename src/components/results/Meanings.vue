<template>
  <ol class="mt-4">
    <li v-for="(meaning, index) in meanings" :key="index">
      <span class="text-white-50"><i>Part of Speech:</i></span>
      {{ meaning.partOfSpeech }}

      <Definitions :definitions="meaning.definitions" />
    </li>
  </ol>
</template>

<script>
import Definitions from "./Definitions.vue";

export default {
  props: ["result"],
  data() {
    return {
      meanings: [],
    };
  },
  methods: {
    mapData() {
      for (const data of this.result) {
        this.meanings.push(...data.meanings);
      }
    },
  },
  components: {
    Definitions,
  },
  created() {
    this.mapData();
  },
};
</script>
