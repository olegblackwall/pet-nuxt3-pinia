<template>
    <div class="modal" tabindex="-1" role="dialog" v-if="is_visible">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Тренировка с reduce</h5>
                    <button type="button" class="close" @click="close_modal">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <form @submit.prevent="calculate_sum">
                        <div class="form-group">
                            <label for="numbers"
                                >Введите числа через запятую</label
                            >
                            <input
                                type="text"
                                id="numbers"
                                v-model="numbers"
                                class="form-control"
                                placeholder="1,2,3,4,5"
                            />
                        </div>
                        <button type="submit" class="btn btn-primary">
                            Вычислить сумму
                        </button>
                    </form>
                    <div v-if="result !== null" class="mt-3">
                        <h5>Результат: {{ result }}</h5>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            is_visible: false,
            numbers: "",
            result: null,
        }
    },
    methods: {
        open_modal() {
            this.is_visible = true
        },
        close_modal() {
            this.is_visible = false
            this.numbers = ""
            this.result = null
        },
        calculate_sum() {
            const num_array = this.numbers.split(",").map(Number)
            this.result = num_array.reduce((acc, num) => acc + num, 0)
        },
    },
}
</script>

<style scoped lang="sass">
.modal
    display: block
    background: rgba(0, 0, 0, 0.5)

.modal-dialog
    margin-top: 10%
</style>
