<template>
    <div v-if="showBanner" class="cookie">
        <p>Мы используем куки для улучшения вашего опыта на сайте. Примите куки?</p>
        <div class="btns">
        <button @click="acceptCookies">Принять</button>
        <button @click="declineCookies">Отклонить</button>
    </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'

export default defineComponent({
    name: 'Cookie',
    setup() {
        const showBanner = ref(true)

        //Узнать про js-cookie
        onMounted(() => {
            if (document.cookie.includes('кука=есть')) {
                showBanner.value = false
            }
        })

        const acceptCookies = () => {
            document.cookie = "кука=есть; path=/; max-age=72000"
            showBanner.value = false
        }

        const declineCookies = () => {
            showBanner.value = false
        }

        return {
            showBanner,
            acceptCookies,
            declineCookies
        }
    }
})
</script>

<style scoped lang="sass">
.cookie
    position: fixed
    bottom: 64px
    left: 50%
    transform: translateX(-50%)
    background-color: #333
    color: #fff
    padding: 10px 20px
    border-radius: 8px
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1)
    z-index: 1000
    display: flex
    flex-direction: column
    justify-content: center
    gap: 16px

.btns
    display: flex
    justify-content: center

button
    background-color: #42b983
    color: #fff
    border: none
    padding: 10px 20px
    margin: 0 5px
    cursor: pointer
    width: 136px
    border-radius: 8px

button:hover
    background-color: #36856d
</style>