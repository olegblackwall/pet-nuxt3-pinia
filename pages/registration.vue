<template>
  <div class="registration-page">
    <h1>Страница регистрации</h1>
    <div class="center-content">
      <button class="open-modal-button" @click="openModal">Авторизация</button>
      <button class="open-modal-button" @click="openModal">Второе модальное окно</button>
      <ModalAuth v-if="isModalOpen" @close="closeModal" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import ModalAuth from '~/src/components/base/modal/modal-auth.vue'

export default defineComponent({
  name: 'RegistrationPage',
  setup() {
    const isModalOpen = ref(false)

    const openModal = () => {
      isModalOpen.value = true
    }

    const closeModal = () => {
      isModalOpen.value = false
    }

    return {
      isModalOpen,
      openModal,
      closeModal
    }
  },

  components: {
    ModalAuth
  }
})
</script>

<style scoped lang="sass">
.registration-page
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