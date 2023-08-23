<template>
  <div class="hero">
    <div class="hero__wrapper wrapper">
      <div class="hero__window">
        <div class="hero__field hero__field--name">
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
        <p class="hero__desc">Frontend разработчик с акцентом на навыки, связанные с дизайном, такие как UI / UX-дизайн, адаптивный дизайн и кроссбраузерная совместимость.</p>
        <ContactButton />
      </div>
    </div>
  </div>
</template>

<script>
import ContactButton from './ContactButton.vue';

export default {
    name: 'HeroSection',
    props: {
        msg: String
    },
    components: { ContactButton }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

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
  margin: 320px auto 120px;
}

.hero__title {
  font-family: 'Neue Machina', Inter, Arial;
  font-size: calc(var(--index)*5);
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
  z-index: -1;
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

</style>
