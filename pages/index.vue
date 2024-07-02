<template>
    <div class="index">
        <h1>Добро пожаловать на главную страницу!</h1>
        <p>Это простая страница, созданная с помощью Nuxt 3.</p>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"

export default defineComponent({
    name: "IndexPage",
    setup() {},
})
</script>

<style scoped lang="sass">
.index
	display: flex
	flex-direction: column
	align-items: center
	justify-content: center
	height: 88vh
	text-align: center

h1
	color: #42b983

p
	color: #2c3e50
</style>
