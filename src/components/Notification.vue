<template>
    <div class="notification">
        <div class="notification__wrapper">
            <button class="notification__close" @click="closeNotificate">
                <img src="../assets/icons/close.svg" alt="close icon" class="notification__icon">
            </button>
            <p class="notification__text">{{ msg }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "NotificationComponent",
    props: {
        msg: {
            type: String,
            default: 'Новое уведомление!',
        }
    },
    methods: {
        closeNotificate(){
            console.log('close notificate');
            this.$emit('close-notificate');
        }
    }
}
</script>

<style scoped lang="scss">
.notification {
    transition: all 0.2s ease-in-out;
    position: fixed;
    bottom: 20px;
    right: 20px;
    width: min(340px, 40%);
}

.notification__wrapper {
    position: relative;
    backdrop-filter: blur(15px);
    background-color: rgba(255, 255, 255, 0.7);
    padding: 20px;
    border-radius: 24px;
}

.notification__text {
    font-size: 22px;
    font-family: 'PP Neue Machina Regular';
    color: black;
}

.notification__close {
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
    background-color: rgb(255, 255, 255);
    padding: 10px;
    border-radius: 15px;
    opacity: 1;
    position: absolute;
    cursor: pointer;
    top: 10px;
    right: 10px;
    opacity: 0.7;
    transition: all .25s ease-in-out;
    &:hover {
        opacity: 1;
        transform: scale(1.05);
    }
}

.notification__icon {
    height: 18px;
    width: 18px;
}
</style>