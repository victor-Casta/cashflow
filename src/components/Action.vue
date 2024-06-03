<template>
    <button @click=" showModal = true ">Agregar movimiento</button>
    <Teleport to="#app">
        <Modal v-show="showModal" @close="showModal = false">
            <form @submit.prevent="submit">
                <div class="field">
                    <label>Titulo</label>
                    <input type="text" v-model="title"></input>
                </div>
                <div class="field">
                    <label>Monto</label>
                    <input type="number" v-model="amount"></input>
                </div>
                <div class="field">
                    <label>Descripcion</label>
                    <textarea rows="4" v-model="desciption"></textarea>
                </div>
                <div class="field">
                    <label>Tipo de movimiento</label>
                    <label class="radio-label">
                        <input type="radio" v-model="movementType" value="Ingreso">
                        <span>Ingreso</span>
                    </label>
                    <label class="radio-label">
                        <input type="radio" v-model="movementType" value="Gasto">
                        <span>Gasto</span>
                    </label>
                </div>
                <div class="action">
                    <button>
                        Agregar movimiento
                    </button>
                </div>
            </form>
        </Modal>
    </Teleport>
</template>

<script setup>
    import { defineComponent, ref, defineEmits } from "vue"
    import Modal from './Modal.vue'

    const showModal = ref(false)
    const title = ref('')
    const amount = ref(0)
    const desciption = ref('')
    const movementType = ref('Ingreso')

    const emit = defineEmits(['create'])

    function aleatoryNumbers() {
    return Math.floor(Math.random() * Number.MAX_SAFE_INTEGER) + 1;
    }

    const submit = () => {
        showModal.value = !showModal.value
        emit('create', {
            title: title.value,
            desciption: desciption.value,
            amount: movementType.value === 'Ingreso' ? amount.value : -amount.value,
            time: new Date(),
            id: aleatoryNumbers()
        })
        title.value = ''
        desciption.value = ''
        amount.value = 0
        movementType.value = 'Ingreso'
    }

</script>

<style scoped>
    button {
        color: white;
        font-size: 1.25rem;
        background-color: #529fdf;
        border: none;
        width: 100%;
        padding: 24px 60px;
        border-radius: 60px;
        box-sizing: border-box;
    }

    form {
        font-size: 1.24rem;
        width: 100%;
    }

    form .action {
        padding: 0 24px;
    }

    .field {
        display: flex;
        justify-content: space-between;
        flex-direction: column;
        padding: 16px 24px;
    }

    label {
        margin-bottom: 8px;
    }

    input,
    textarea {
        font-size: 1.24rem;
        border: 2px solid #529fdf;
        border-radius: 8px;
        padding: 8px;
    }

    input[type="number"] {
        text-align: right;
    }

    .radio-label {
        display: flex;
        align-items: center;
        margin-top: 8px;
    }

    .radio-label span {
        margin-top: 4px;
        margin-left: 8px;
    }

    input[type="radio"] {
        appearance: none;
        width: 1.24rem;
        height: 1.24rem;
        color: #529fdf;
        border: 2px solid #529fdf;
        border-radius: 50%;
    }

    input[type="radio"]:checked {
        background-color: #529fdf;
    }
</style>