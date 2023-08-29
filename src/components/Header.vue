<template>
    <header class="header">
        <div class="header__wrapper wrapper">
            <a href="/" class="header__logo logo">
                <p class="logo__title visually-hidden">Главная страница</p>
                <img src="../assets/icons/logo.svg" alt="logo image" class="logo__image">
            </a>
            <nav class="header__navigate navigate">
                <a href="https://github.com/akiverin" class="navigate__link" target="_blank">GitHub</a>
                <a href="https://vk.com/andkiv" class="navigate__link" target="_blank">VK</a>
                <a href="https://behance.net/kiverin03fb9c" class="navigate__link" target="_blank">Behance</a>
            </nav>
        </div>
    </header>
</template>

<script>
export default {
    name: "HeaderComponent",
}
</script>

<style scoped lang="scss">

.header__wrapper {
    display: flex;
    justify-content: space-between;
    padding: 20px 20px;
    align-items: center;
}
.logo__image {
    width: 64px;
}

.navigate {
    display: flex;
    gap: 60px;
}

.navigate__link {
    color: #FFF;
    font-family: 'PP Neue Machina Regular', Inter, arial, sans-serif;
    font-size: 22px;
    font-weight: 400;
    line-height: 1.5;
    text-decoration: none;
    &:hover {
        text-decoration: underline;
        color: rgb(49, 189, 214);
    }
}
</style>