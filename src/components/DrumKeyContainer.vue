<template>
  <div class="key-container">
    <drumkey v-for="config in keyConfigs"
    :key="`drumkey-${config.key}`"
    :keyIdent="config.key"
    :soundDescription="config.sound"
    ref="drumkeys"></drumkey>
  </div>
</template>

<script>
import drumkey from './DrumKey'

export default {
  name: 'keycontainer',
  components: {
    drumkey
  },
  props: {
    keyConfigs: {
      required: true,
      validator(value) {
        return Array.isArray(value) && value.length &&
        value.every(config=>config.key && config.sound);
      }
    }
  },
  created() {
    window.addEventListener("keypress", (event)=>{
      let instance = this.$refs.drumkeys
      .find(instance=>instance.keyCode === event.keyCode)

      return instance && instance.play();
    });
  }
}
</script>

<style scoped>
.key-container {
  background-image: url("../../static/images/concert2.png");
  background-size: cover;
  display: flex;
  flex: 1;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
}
</style>
