<template>
  <section class="hero">
    <div class="hero__wrapper wrapper">
      <div class="hero__window">
        <div class="hero__field hero__field--name">
          <div class="hero__badges badges">
            <Badge>team-work</Badge>
            <Badge>design</Badge>
            <Badge>mobile</Badge>
          </div>
          <h1 class="hero__title">Андрей</h1>
          <img src="../assets/icons/fillStar.svg" alt="star icon descorate" class="hero__icon hero__icon--fillStar">
        </div>
        <div class="hero__field hero__field--post">
          <h1 class="hero__title hero__title--italic">frontend</h1>
          <img src="../assets/icons/arrow.svg" alt="arrow icon descorate" class="hero__icon hero__icon--arrow">
        </div>
        <div class="hero__field hero__field--surname">
          <img src="../assets/icons/strokeStar.svg" alt="star icon descorate" class="hero__icon hero__icon--strokeStar">
          <h1 class="hero__title">Киверин</h1>
        </div>
      </div>
      <div class="hero__info">
        <p class="hero__desc">
          Frontend разработчик с&nbsp;акцентом на&nbsp;навыки, связанные с&nbsp;дизайном, такие как UI&nbsp;/ UX-дизайн, адаптивный дизайн и&nbsp;кроссбраузерная совместимость.        </p>
        <Button>Связаться</Button>
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
  padding: 0 5%;
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
  font-size: 22px;
  width: 50%;
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

@media screen and (max-width: 768px){
  .hero__title {
    font-size: 92px;
    &--italic {
      font-size: 72px;
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
      left: -10%;
    }
    &--arrow {
      transform: scale(0.8);
      top: 0px;
      right: -180px;
    }
  }

  .badges {
    position: absolute;
    left: -100px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    z-index: -1;
  }
}
</style>
