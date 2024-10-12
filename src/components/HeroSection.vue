<template>
  <section class="hero">
    <div class="hero__wrapper wrapper">
      <div class="hero__window" data-scroll-section>
        <div class="hero__field hero__field--name">
          <div class="hero__badges badges" data-scroll data-scroll-speed=".1">
            <Badge>team-work</Badge>
            <Badge>design</Badge>
            <Badge>mobile</Badge>
          </div>
          <h1 class="hero__title" data-scroll data-scroll-speed=".15">Андрей</h1>
          <img src="../assets/icons/fillStar.svg" alt="star icon descorate" class="hero__icon hero__icon--fillStar"
            data-scroll data-scroll-speed=".2">
        </div>
        <div class="hero__field hero__field--post">
          <h1 class="hero__title hero__title--italic" data-scroll data-scroll-speed=".25">frontend</h1>
          <img src="../assets/icons/arrow.svg" alt="arrow icon descorate" class="hero__icon hero__icon--arrow"
            data-scroll data-scroll-speed=".25">
        </div>
        <div class="hero__field hero__field--surname">
          <img src="../assets/icons/strokeStar.svg" data-scroll data-scroll-speed=".15" alt="star icon descorate"
            class="hero__icon hero__icon--strokeStar">
          <h1 class="hero__title" data-scroll data-scroll-speed=".35">Киверин</h1>
        </div>
      </div>
      <div class="hero__info">
        <p class="hero__desc">
          Frontend разработчик, веб-дизайнер (UI&nbsp;/ UX-дизайн). React и Vue – основные фрейморки для проектов.
          Практикую fullstack и мобильную разработку (React Native), прокачиваю soft-скиллы.</p>
        <Button url="#contact">Связаться</Button>
      </div>
    </div>
    <img src="../assets/icons/line.svg" alt="" class="hero__line">
  </section>
</template>

<script>
import Badge from './Badge.vue';
import Button from './Button.vue';


export default {
  name: 'HeroSection',
  props: {
    msg: String
  },
  components: { Badge, Button }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.hero {
  position: relative;
  margin-bottom: 60px;
}

.hero__wrapper {
  display: flex;
  flex-direction: column;
  gap: 0px;
}

.hero__window {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  max-width: 80%;
  margin: 160px auto 120px;
}

.hero__title {
  font-family: 'Neue Machina', Inter, Arial;
  font-size: 148px;
  text-transform: uppercase;
  margin: 0;
  padding: 0;
  text-align: right;

  &--italic {
    font-family: PP Migra Italic Extrabold Italic, serif;
    font-weight: 800;
    color: #EC6FD5;
  }
}

.hero__info {
  border-top: 1px solid white;
  width: 100%;
}

.hero__field {
  position: relative;
  height: fit-content;
  width: fit-content;

  &--post {
    margin-right: 180px;
  }

  &--surname {
    // margin-right: 240px;
  }
}

.hero__icon {
  position: absolute;
  z-index: -2;

  &--fillStar {
    top: -80px;
    left: 40%;
  }

  &--strokeStar {
    top: -5%;
    left: -20%;
  }

  &--arrow {
    top: 20px;
    right: -180px;
  }
}

.hero__info {
  display: flex;
  flex: 0 0 auto;
  place-content: center space-between;
  align-items: center;
}

.hero__desc {
  font-family: 'PP Neue Machina Regular';
  font-size: 18px;
  width: 52%;
  text-align: left;
  line-height: 1.5;
}

.hero__line {
  bottom: -360px;
  flex: 0 0 auto;
  left: -300px;
  position: absolute;
  width: 1187px;
  z-index: -2;
}

.badges {
  position: absolute;
  left: -204px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  z-index: -1;
}


@media screen and (max-width: 1080px) {

  .hero__title {
    font-size: 100px;

    &--italic {
      font-size: 100px;
    }
  }

  .hero__desc {
    font-size: 18px;
  }

  .hero__field {
    width: 100%;
    margin-right: 20px;
  }

  .hero__icon {
    position: absolute;
    z-index: -2;

    &--fillStar {
      top: -80px;
      left: 40%;
    }

    &--strokeStar {
      top: -5%;
      left: -10%;
    }

    &--arrow {
      transform: scale(0.8);
      top: 0px;
      right: -180px;
    }
  }

  .badges {
    transform: scale(0.7);
    position: absolute;
    top: -20px;
    left: -40px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    z-index: -1;
  }
}

@media screen and (max-width: 768px) {

  .hero__title {
    font-size: 92px;

    &--italic {
      font-size: 72px;
    }
  }

  .hero__desc {
    font-size: 16px;
  }

  .hero__field {
    transform: scale(0.8);
    width: 100%;
    margin-right: 20px;
  }

  .hero__icon {
    position: absolute;
    z-index: -2;

    &--fillStar {
      top: -80px;
      left: 40%;
    }

    &--strokeStar {
      top: -5%;
      left: -10%;
    }

    &--arrow {
      transform: scale(0.8);
      top: 0px;
      right: -180px;
    }
  }

  .badges {
    opacity: 0;
    transform: scale(0.7);
    position: absolute;
    top: -20px;
    left: -140px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    z-index: -1;
  }
}

@media screen and (max-width: 560px) {


  .hero__title {
    display: flex;
    place-content: center;
    font-size: 64px;
    line-height: 1;

    &--italic {
      font-size: 70px;
      display: flex;
      place-content: center;
    }
  }

  .hero__field {
    transform: scale(0.8);
    width: 100%;
    margin: 0;
  }

  .hero__info {
    flex-direction: column;
    gap: 12px;
  }

  .hero__desc {
    width: 100%;
    font-size: 16px;
  }

  .badges {
    position: absolute;
    top: 200px;
    left: 100px;
    display: flex;
    text-align: center;
    align-items: center;
    flex-direction: column;
    gap: 8px;
    z-index: -1;
  }

  .hero__icon {
    width: 10em;
  }
}
</style>
