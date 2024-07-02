<template>
    <div v-if="is_open" class="modal-overlay" @click="close_modal">
        <div class="modal-content" @click.stop>
            <button class="close-button" @click="close_modal">X</button>
            <component
                class="modal-container"
                :is="modal_component"
                @close="close_modal"
            />
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import ModalAuth from "~/src/components/base/modal/modal-auth.vue"
import ModalReduce from "~/src/components/base/modal/modal-reduce.vue"

export default defineComponent({
    name: "Modal",
    props: {
        is_open: {
            type: Boolean,
            required: true,
        },
        modal_component: {
            type: Object,
            required: true,
        },
    },
    setup(props, { emit }) {
        const close_modal = () => {
            emit("close")
        }

        return {
            close_modal,
        }
    },
    components: {
        ModalAuth,
        ModalReduce,
    },
})
</script>

<style scoped lang="sass">
.modal-overlay
    position: fixed
    top: 0
    left: 0
    width: 100%
    height: 100%
    background-color: rgba(0, 0, 0, 0.6)
    display: flex
    justify-content: center
    align-items: center

.modal-content
    position: relative
    width: fit-content
    height: fit-content
    background-color: #fff
    padding: 20px
    border-radius: 8px
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.4)
    text-align: center

.close-button
    position: absolute
    top: -15px
    right: -15px
    width: 30px
    height: 30px
    background-color: #42b983
    border-radius: 50%
    font-size: 1.2rem
    line-height: 30px
    text-align: center
    cursor: pointer
    z-index: 999
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.3)
</style>
