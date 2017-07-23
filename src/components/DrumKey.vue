<template>
  <div class="key" @click="play" :class="{playing}" @transitionend="revertTransition">
    <kbd>{{keyIdent}}</kbd>
    <span class="sound-description">{{soundDescription}}</span>
    <audioplay :playing="playing" :src="`static/sounds/${soundDescription}.wav`"></audioplay>
  </div>
</template>

<script>
import audioplay from "./AudioPlay";

export default {
  name: 'drumkey',
  components: {
    audioplay
  },
  data() {
    return {playing: false};
  },
  methods: {
    play() {
      this.playing = true;
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
    keyCode() {
      return this.keyIdent.charCodeAt();
    }
  },
}
</script>

<style scoped>
.key {
  border: 2px solid black;
  border-radius: 3px;
  margin: auto;
  font-size: 1rem;
  transition: all .07s ease;
  width: 5rem;
  text-align: center;
  color: white;
  background: rgba(0,0,0,0.4);
  text-shadow: 0 0 .5rem black;
}
@media (min-width: 65rem) {
  .key {
    font-size: 3rem;
    border: .4rem solid black;
    border-radius: .5rem;
  }
}

.playing {
  transform: scale(1.1);
  border-color: #ffc600;
  box-shadow: 0 0 1rem #ffc600;
}

kbd {
  display: block;
}

.sound-description {
  font-size: 0.5rem;
  letter-spacing: .1rem;
  color: #ffc600;
}
@media (min-width: 40rem) {
  .sound-description {
    font-size: 1.5rem;
  }
}
</style>
