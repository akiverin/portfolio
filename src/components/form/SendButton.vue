<template>
    <button class="button" type="submit"><slot></slot></button>
</template>

<script>
export default {
    name: "SendButtonComponent",
}
</script>

<style scoped lang="scss">
.button {
    cursor: pointer;
    font-family: 'PP Neue Machina Regular';
    min-height: 64px;
    border: 1px solid transparent;
    color: #020202;
    background-color: #f1f1f1;
    border-radius: 12px;
    margin-top: 12px;
    font-size: 24px;
    font-weight: 500;
    transition: all .5s;
    margin: 10px;
    &:hover {
        color: #f1f1f1;
        background-color: transparent;
        border: 1px solid #f1f1f1;
    }
}

@media screen and (max-width: 560px){
        .button {
            font-size: 20px;
        }
    }
</style>