<template>
    <div class="auth-page">
        <h1>Страница авторизации</h1>
        <div class="center-content">
            <button class="open-modal-button" @click="openModal('auth')">
                Авторизация
            </button>
            <button class="open-modal-button" @click="openModal('reduce')">
                reduce(acc, item, index, arr)
            </button>
            <Modal
                v-if="current_modal"
                :is_open="true"
                :modal_component="current_modal"
                @close="closeModal"
            />
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"
import Modal from "~/src/components/base/modal/modal.vue"

export default defineComponent({
    name: "AuthPage",
    setup() {
        const current_modal = ref<any>(null)

        const openModal = (modal_name: string) => {
            if (modal_name === "auth") {
                current_modal.value = "ModalAuth"
            } else if (modal_name === "reduce") {
                current_modal.value = "ModalReduce"
            }
        }

        const closeModal = () => {
            current_modal.value = null
        }

        return {
            current_modal,
            openModal,
            closeModal,
        }
    },

    components: {
        Modal,
    },
})
</script>

<style scoped lang="sass">
.auth-page
    display: flex
    flex-direction: column
    gap: 20px
    justify-content: center
    align-items: center
    height: 88vh

h1
    color: #42b983

.center-content
    display: flex
    gap: 1rem
    max-width: 800px
    text-align: center

.open-modal-button
    background-color: #42b983
    color: #fff
    border: none
    padding: 10px 20px
    font-size: 1rem
    cursor: pointer
    transition: background-color 0.3s
    border-radius: .5rem

.open-modal-button:hover
    background-color: #36856d
</style>
