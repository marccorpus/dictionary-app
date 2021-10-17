<template>
  <div>
    <b-button
      variant="warning"
      size="sm"
      class="shadow-none"
      @click="playPronounciation"
      :disabled="!audio"
      ><b-icon :icon="buttonIcon"></b-icon> {{ buttonCaption }}</b-button
    >
    <audio ref="audio">
      <source :src="audio" type="audio/mpeg" />
      Your browser does not support the audio element.
    </audio>
  </div>
</template>

<script>
export default {
  props: ["audio"],
  computed: {
    buttonIcon() {
      return this.audio ? "volume-up" : "volume-mute";
    },
    buttonCaption() {
      return this.audio ? "Pronounciation" : "No audio available";
    },
  },
  methods: {
    playPronounciation() {
      this.$refs.audio.load();
      this.$refs.audio.play();
    },
  },
};
</script>
