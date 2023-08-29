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
        background: linear-gradient(164deg, #24BCD7 0%, #50E9FF 100%);
    }
</style>