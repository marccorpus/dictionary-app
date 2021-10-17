<template>
  <div>
    <ul v-for="(definition, index) in definitions" :key="index" class="my-3">
      <li>
        <span class="text-white-50"><i>Definition:</i></span>
        {{ definition.definition }}

        <Synonyms :synonyms="definition.synonyms" />
      </li>
    </ul>
  </div>
</template>

<script>
import Synonyms from "./Synonyms.vue";

export default {
  props: ["definitions"],
  components: {
    Synonyms,
  },
};
</script>
