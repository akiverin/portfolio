<template>
  <div class="window" :style="{ transform: `translateX(${rotation}%) translateY(${rotation*2}%) translateZ(0px)` }"></div>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

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
    HelloWorld
  },
}
</script>

<style lang="scss">
body {
  background-color: rgb(26, 24, 30);
  padding: 0;
  margin: 0;
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
  color: #2c3e50;
  margin-top: 60px;
  overflow: hidden;
  padding: 0;
  margin: 0;
}
</style>
