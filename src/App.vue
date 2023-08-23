<template>
  <div class="window" :style="{ transform: `translateX(${rotation}%) translateY(${rotation*2}%) translateZ(0px)` }"></div>
  <HeroSection msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HeroSection from './components/HeroSection.vue';

export default {
  name: 'App',
  data() {
    return {
      rotation: 0,
    };
  },
  mounted() {
    var self = this;
    setInterval(function () {
      self.rotation = Math.floor(Math.random()*10);
    }, 100);
  },
  components: {
    HeroSection
},
}
</script>

<style lang="scss">
body {
  background-color: rgb(26, 24, 30);
  padding: 0;
  margin: 0;
  @font-face {
    font-family: 'Migra Italic';
    src: local('Migra Italic'), local('Migra Italic'),
        url('assets/PP-Migra-Italic-Extrabold-Italic.ttf') format('ttf');
    font-weight: 800;
    font-style: normal;
  }
  @font-face{
    src:url(https://framerusercontent.com/modules/assets/4thwIOvYFOFhAXrzDsrImh1qlw~qwrXOQhxSB17CsgJlKQ2QlaYBYgSiTSToshyFBLf52I.ttf);
    font-family:PP Migra Italic Extrabold Italic}
  @font-face{src: local('Neue Machina Ultra bold'), local('Neue-Machina-Ultra-bold'),
        url('assets/PPNeueMachina-Regular.otf') format('woff2');
    font-family: 'PP Neue Machina Regular'
  }
  @font-face {
    font-family: 'Neue Machina';
    src: local('Neue Machina Ultra bold'), local('Neue-Machina-Ultra-bold'),
        url('assets/NeueMachina-Ultrabold.woff2') format('woff2');
    font-weight: 800;
    font-style: normal;
  }

}
.window {
  background: url("https://framerusercontent.com/images/rR6HYXBrMmX4cRpXfXUOvpvpB0.png");
  opacity: 0.1;
  inset: -200%;
  width: 400%;
  height: 400%;
  position: absolute;
  z-index: -1;
}

#app {
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

:root {
  --index: calc(1vh + 1vw);
}

.wrapper {
  max-width: 1400px;
  margin: 0 auto;
}
</style>
