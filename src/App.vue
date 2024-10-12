<template>
  <Header />
  <main class="main" data-scroll-container>
    <div class="main__wrapper">
      <HeroSection data-scroll-section data-scroll-delay="0.2" />
      <ProjectsSection data-scroll-section />
      <StackSection data-scroll-section data-persistent />
      <AchievementsSection data-scroll-section />
      <ContactSection data-scroll-section id="contact" @notificate-new="sendNotification" />
    </div>
  </main>
  <Footer />
  <div class="background">
    <div class="background__shadow"></div>
    <div class="background__frame"></div>
    <div class="background__noisy noisy"
      :style="{ transform: `translateX(${rotation}%) translateY(${rotation * 2}%) translateZ(0px)` }"></div>
  </div>
  <Notification v-show="this.notification != ''" :msg="notification"
    @close-notificate="() => { this.notification = '' }" />
</template>

<script>
import AchievementsSection from './components/AchievementsSection.vue';
import ContactSection from './components/ContactSection.vue';
import Footer from './components/Footer.vue';
import Header from './components/Header.vue';
import HeroSection from './components/HeroSection.vue';
import Notification from './components/Notification.vue';
import ProjectsSection from './components/ProjectsSection.vue';
import StackSection from './components/StackSection.vue';

import LocomotiveScroll from 'locomotive-scroll';
new LocomotiveScroll({
  el: document.querySelector('[data-scroll-container]'),
  smooth: true,
  multiplier: 0.1,
  class: 'main',
  repeat: true,
  duration: 1.2,
});

export default {
  name: 'App',
  data() {
    return {
      rotation: 0,
      notification: '',
    };
  },
  mounted() {
    var self = this;
    setInterval(
      function () {
        self.rotation = Math.floor(Math.random() * 10);
      },
      100);
  },
  methods: {
    sendNotification() {
      this.notification = "Письмо отправлено!";
      setTimeout(() => {
        this.notification = "";
      }, 15000);
    }
  },
  components: {
    HeroSection,
    Header,
    ProjectsSection,
    AchievementsSection,
    ContactSection,
    Notification,
    StackSection,
    Footer
  },
}
</script>

<style lang="scss">
body {
  background-color: rgb(26, 24, 30);
  scroll-behavior: smooth;
  padding: 0;
  margin: 0;
  font-size: 1vw;

  @font-face {
    font-family: 'Migra Italic';
    src: local('Migra Italic'), local('Migra Italic'),
      url('assets/PP-Migra-Italic-Extrabold-Italic.ttf') format('ttf');
    font-weight: 800;
    font-style: normal;
  }

  @font-face {
    src: url(https://framerusercontent.com/modules/assets/4thwIOvYFOFhAXrzDsrImh1qlw~qwrXOQhxSB17CsgJlKQ2QlaYBYgSiTSToshyFBLf52I.ttf);
    font-family: PP Migra Italic Extrabold Italic
  }

  @font-face {
    src: local('Neue Machina Ultra bold'), local('Neue-Machina-Ultra-bold'),
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

.background__shadow {
  z-index: -2;
  position: absolute;
  top: 3170px;
  background: -webkit-linear-gradient(180deg, rgba(26, 24, 30, 0), rgb(26, 24, 30));
  background: -moz-linear-gradient(180deg, rgba(26, 24, 30, 0), rgb(26, 24, 30));
  background: linear-gradient(180deg, rgba(26, 24, 30, 0), rgb(26, 24, 30));
  width: 100%;
  height: 200px;
}

.background__frame {
  top: 3370px;
  z-index: -2;
  background-color: rgb(26, 24, 30);
  position: absolute;
  height: 100%;
  width: 100%;
}

.noisy {
  background: url("https://framerusercontent.com/images/rR6HYXBrMmX4cRpXfXUOvpvpB0.png");
  opacity: 0.1;
  inset: -200%;
  width: 400%;
  height: 400%;
  position: absolute;
  z-index: -3;
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
  padding: 0 5%;
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  border: 0;
  padding: 0;
  white-space: nowrap;
  clip-path: inset(100%);
  clip: rect(0 0 0 0);
  overflow: hidden;
}
</style>
