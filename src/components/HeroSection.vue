<template>
  <div class="hero">
    <h1 class="hero__title">Андрей</h1>
    <h1 class="hero__title hero__title--italic">fontend-dev</h1>
    <h1 class="hero__title">Киверин</h1>
    <div class="hero__info">
      <p class="hero__desc">Frontend разработчик с акцентом на навыки, связанные с дизайном, такие как UI / UX-дизайн, адаптивный дизайн и кроссбраузерная совместимость.</p>
      <ContactButton />
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

.hero__title {
  font-family: 'Neue Machina', Inter, Arial;
  font-size: 90px;
  text-transform: uppercase;
  &--italic {
    font-family: PP Migra Italic Extrabold Italic, serif;
    font-weight: 800;
  }
}


</style>
