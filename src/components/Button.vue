<template>
    <button class="button"><slot></slot></button>
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
}
</style>