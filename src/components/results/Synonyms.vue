<template>
  <div class="my-2" v-if="synonyms.length > 0">
    <span class="text-white-50"><i>Synonyms:</i></span>
    <b-badge
      class="badge"
      variant="warning"
      v-for="(synonym, index) in synonyms"
      :key="index"
      >{{ synonym }}</b-badge
    >
  </div>
</template>

<script>
export default {
  props: ["synonyms"],
};
</script>

<style scoped>
.badge {
  background-color: #17a2b8;
  color: #fff;
  margin: 0 5px;
}
</style>
