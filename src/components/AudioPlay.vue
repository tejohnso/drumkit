<template>
  <audio :playing="playing" :src="src"></audio>
</template>

<script>
export default {
  name: 'audioplay',
  props: {
    playing: {required: true, type: Boolean},
    src: {required: true, type: String}
  },
  watch: {
    playing(playing) {
      if (!playing) {return;}
      this.$el.currentTime = 0;
      this.$el.play();
    },
  },
}
</script>
