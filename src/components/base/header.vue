<template>
    <header class="header">
        <nav class="nav">
            <ul class="nav-list">
                <li class="nav-item">
                    <NuxtLink to="/" class="nav-button">Главная</NuxtLink>
                </li>
                <li class="nav-item">
                    <NuxtLink to="/auth" class="nav-button"
                        >Авторизация</NuxtLink
                    >
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
// Здесь можно добавить вашу логику компонента, если это необходимо
</script>

<style scoped lang="sass">
.header
    background-color: #42b983
    padding: 1rem

.nav
    display: flex
    justify-content: flex-end

.nav-list
    display: flex
    justify-content: space-between
    list-style-type: none
    margin: 0
    padding: 0
    display: flex
    align-items: center
    width: 100%

.nav-item
    margin-left: 1rem

.nav-button
    background-color: #fff
    border: none
    color: #42b983
    padding: 0.5rem 1rem
    font-size: 1rem
    cursor: pointer
    transition: background-color 0.3s, color 0.3s
    text-decoration: none
    border-radius: .5rem

.nav-button:hover
    background-color: #42b983
    color: #fff
</style>
