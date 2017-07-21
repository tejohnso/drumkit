<template>
  <div id="app">
    <drumkeycontainer :keyConfigs="keyConfigs"></drumkeycontainer>
  </div>
</template>

<script>
import drumkeycontainer from './components/DrumKeyContainer'

export default {
  name: 'app',
  components: {
    drumkeycontainer
  },
  data() {
    return {
      keyConfigs: [
        {key: 'a', sound: 'clap'},
        {key: 's', sound: 'boom'},
        {key: 'd', sound: 'hihat'},
        {key: 'f', sound: 'kick'},
        {key: 'g', sound: 'tink'},
        {key: 'h', sound: 'tom'},
        {key: 'j', sound: 'open'},
        {key: 'k', sound: 'ride'},
        {key: 'l', sound: 'snare'},
      ]
    }
  }
}
</script>

<style>
div#app {background-color: grey;}
</style>
