<template>
    <div>
        <Header />
        <NuxtPage />
        <Footer />
        <Cookie 
            v-if="showCookie"
        />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Header from '~/src/components/base/header.vue'
import Footer from '~/src/components/base/footer.vue'
import Cookie from '~/src/components/base/cookie.vue'

export default defineComponent ({
    name: 'DefaultLayout',
    setup() {
        const showCookie = ref(false)

        onMounted(() => {
            setTimeout(() => {
                showCookie.value = true
            }, 1000)
        })

        return {
        showCookie
        }
    },
    components: {
        Header,
        Footer,
        Cookie
    }
})
</script>

<style scoped>
/* Здесь можно добавить стили для лейаута */
</style>