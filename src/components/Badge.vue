<template>
    <div class="badge">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'BadgeComponent',
}
</script>

<style scoped lang="scss">
.badge {
    border-radius: 24px;
    color: #000;
    font-family: 'PP Neue Machina Regular';
    font-weight: 800;
    font-size: 22px;
    width: fit-content;
    padding: 6px 10px;
    background: linear-gradient(164deg, #369ed6d8 0%, #50e8ffd7 100%);

    @media screen and (max-width: 560px) {
        font-size: 16px;
        padding: 2px 4px;
    }
}
</style>