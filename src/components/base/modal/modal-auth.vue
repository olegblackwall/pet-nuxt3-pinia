<template>
    <h2>Авторизация</h2>
    <form @submit.prevent="handleSubmit">
        <div class="form-group">
            <label for="email">Email:</label>
            <input id="email" type="email" v-model="email" required />
        </div>
        <div class="form-group">
            <label for="password">Пароль:</label>
            <input id="password" type="password" v-model="password" required />
        </div>
        <div class="button-group">
            <button class="btn-submit" type="submit">Отправить</button>
            <button class="btn-cancel" @click="closeModal">Отмена</button>
        </div>
    </form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"

export default defineComponent({
    name: "ModalAuth",
    props: {
        isOpen: {
            type: Boolean,
            default: false,
        },
    },
    emits: ["close", "auth"],
    setup(props, { emit }) {
        const email = ref("")
        const password = ref("")

        const handleSubmit = () => {
            // Действия по отправке данных (например, вызов метода авторизации)
            emit("auth", { email: email.value, password: password.value })
            closeModal()
        }

        const closeModal = () => {
            emit("close")
            // Очистка полей формы при закрытии модального окна
            email.value = ""
            password.value = ""
        }

        return {
            email,
            password,
            handleSubmit,
            closeModal,
        }
    },
})
</script>

<style scoped lang="sass">

h2
    font-size: 1.5rem
    margin-bottom: 1rem

form
    display: flex
    flex-direction: column
    align-items: center
    width: 400px

.form-group
    margin-bottom: 1rem
    width: 100%

label
    font-weight: bold
    display: block
    margin-bottom: 0.5rem
    text-align: left

input[type="email"],
input[type="password"]
    width: 100%
    padding: 0.5rem
    font-size: 1rem
    border: 1px solid #ccc
    border-radius: 4px
    outline: none
    transition: border-color 0.3s

input[type="email"]:focus,
input[type="password"]:focus
    border-color: #42b983

.button-group
    margin-top: 1rem
    display: flex
    gap: 1rem

button
    width: 8rem
    padding: 0.75rem 1.5rem
    font-size: 1rem
    cursor: pointer
    border: none
    border-radius: 4px
    transition: background-color 0.3s

.btn-submit
    background-color: #42b983
    color: #fff

.btn-submit:hover
    background-color: #36856d

.btn-cancel
    background-color: #f44336
    color: #fff

.btn-cancel:hover
    background-color: #d32f2f
</style>
