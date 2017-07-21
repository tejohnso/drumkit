<template>
  <div class="key" :class="{playing}" @transitionend="revertTransition">
    <kbd>{{keyIdent}}</kbd>
    <span class="sound-description">{{soundDescription}}</span>
    <audio :src="`static/sounds/${soundDescription}.wav`" ref="aud"></audio>
  </div>
</template>

<script>
export default {
  name: 'drumkey',
  data() {
    return {playing: false};
  },
  methods: {
    play() {
      this.playing = true;
      let audio = this.$refs.aud;
      audio.currentTime = 0;
      audio.play();
    },
    revertTransition(a) {
      this.playing = false;
    }
  },
  props: {
    keyIdent: { type: String, required: true },
    soundDescription: { type: String, required: true },
  },
  computed: {
    charCode() {
      return this.keyIdent.charCodeAt() - 32;
    }
  },
}
</script>

<style scoped>
.key {
  border: .4rem solid black;
  border-radius: .5rem;
  margin: 1rem;
  font-size: 1rem;
  padding: 0.5rem .5rem;
  transition: all .07s ease;
  width: 5rem;
  text-align: center;
  color: white;
  background: rgba(0,0,0,0.4);
  text-shadow: 0 0 .5rem black;
}

.playing {
  transform: scale(1.1);
  border-color: #ffc600;
  box-shadow: 0 0 1rem #ffc600;
}

kbd {
  display: block;
  font-size: 3rem;
}

.sound-description {
  font-size: 1.2rem;
  text-transform: uppercase;
  letter-spacing: .1rem;
  color: #ffc600;
}
</style>
