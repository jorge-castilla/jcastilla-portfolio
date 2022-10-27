<template>

    <div>
        <b-modal id="modal-contact" hide-footer hide-header>
            
            <h5 class="my-2 mx-2">¡Hablemos!</h5>
            <b-row class="my-2 mx-2" v-for="input in inputs" :key="input.input">

                <label v-if="input.input != 'Mensaje'" :for="input.input">{{ input.input }}:</label>

                <b-form-input v-if="input.input != 'Mensaje'" :id="`type-${input.input}`" :type="input.type" v-model="input.value">
                </b-form-input>

                <b-form-textarea v-else id="textarea" v-model="input.value" placeholder="Escribe tu mensaje..." rows="3"
                    max-rows="6"></b-form-textarea>


            </b-row>
            <button @click="sendForm" class="my-2 mx-2">Enviar</button>

        </b-modal>
    </div>
</template>

<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script>
export default {
    data() {
        return {
            inputs: [
                { 'input': 'Nombre', 'type': 'text', 'value': '' },
                { 'input': 'Email', 'type': 'email', 'value': '' },
                { 'input': 'Asunto', 'type': 'text', 'value': '' },
                { 'input': 'Mensaje', 'type': 'text', 'value': '' },
            ]
        }
    },
    methods: {
        sendForm() {
            this.$bvModal.hide('modal-contact');
        }
    }

}
</script>

<style>

</style>