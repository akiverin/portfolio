<template>
    <button class="hero__contact">Связаться</button>
</template>

<script>
export default {
    name: "ContactButton",
    props: {
        msg: {
        type: String,
    },
},
}
</script>

<style scoped lang="scss">
.hero__contact {
  cursor: pointer;
  display: flex;
  width: 171px;
  height: 70px;
  padding: 23px 46px 23px 32px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: none;
  border-radius: 50px;
  background: linear-gradient(146deg, #EC34D9 0%, #681CE3 100%);
  color: #FFF;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: 1.2;
}
</style>