<template>

    <div>
        <b-modal id="modal-contact" hide-footer hide-header>


            <h5 class="my-2 mx-2">¡Hablemos!</h5>
            <b-row class="my-2 mx-2" v-for="input in inputs" :key="input.input">

                <label v-if="input.input != 'Mensaje'" :for="input.input">{{ input.input }}:</label>

                <b-form-input v-if="input.input != 'Mensaje'" :id="`type-${input.input}`" :type="input.type"
                    v-model="input.value">
                </b-form-input>

                <b-form-textarea v-else id="textarea" v-model="input.value" placeholder="Escribe tu mensaje..." rows="3"
                    max-rows="6"></b-form-textarea>


            </b-row>
            <button @click="sendEmail" class="my-2 mx-2">Enviar</button>

        </b-modal>
    </div>
</template>

<script>
import axios from 'axios';

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
       async sendEmail() {
            var data = {
                service_id: 'service_ofkczni',
                template_id: 'template_2u4jly3',
                user_id: 'oLoYhzJdcjeEdg91w',
                template_params: {
                    'name': this.inputs[0].value,
                    'email': this.inputs[1].value,
                    'subject': this.inputs[2].value,
                    'message': this.inputs[3].value
                }
            };
            var config = {
                method: 'post',
                url: 'https://api.emailjs.com/api/v1.0/email/send',
                headers: {
                    'Content-Type': 'application/json',
                    'Access-Control-Request-Headers': '*',
                },
                data: data
            };
            try {
                const response = await axios(config);
                console.log(response);
                this.$bvModal.hide('modal-contact');
            } catch (error) {
                console.log(error);
            }


        }
    }

}
</script>

<style>

</style>