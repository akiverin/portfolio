<template>
    <a class="button" data-scroll data-scroll-to="#contact"><slot></slot></a>
</template>

<script>
export default {
    name: "ButtonComponent",
}
</script>

<style scoped lang="scss">
.button {
    cursor: pointer;
    display: flex;
    padding: 23px 32px;
    text-decoration: none;
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
    font-family: 'Neue Machina', Inter, Arial;
    transition: all 200ms ease-in-out;
    &:hover {
        transform: scale(1.04);
    }
    &::placeholder {
        color: #f1f1f1;
    }
}
</style>