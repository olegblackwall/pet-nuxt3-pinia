<template>
    <div class="layout-container">
        <Header />
        <main class="content">
            <NuxtPage />
        </main>
        <Footer />
        <Cookie v-if="show_cookie" />
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'
import Header from '~/src/components/base/header.vue'
import Footer from '~/src/components/base/footer.vue'
import Cookie from '~/src/components/base/cookie.vue'

export default defineComponent({
    name: 'DefaultLayout',
    setup() {
        const show_cookie = ref<boolean>(false)

        onMounted(() => {
            setTimeout(() => {
                show_cookie.value = true
            }, 1000)
        })

        return {
            show_cookie
        }
    },
    components: {
        Header,
        Footer,
        Cookie
    }
})
</script>

<style scoped lang="sass">
.layout-container
    display: flex
    flex-direction: column
    min-height: 100vh
    background-color: #f5f5f5 // Фоновый цвет для всего макета
    color: #333 // Основной цвет текста

.content
    flex: 1
    background-color: #fff // Цвет фона для основного контента
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1)

@media (max-width: 768px)
    .content
        padding: 1rem
        margin: 0.5rem
</style>
