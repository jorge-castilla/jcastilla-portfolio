<template>

    <div>
        <b-modal id="modal-contact" hide-footer hide-header>

            <b-row class="my-2 mx-2 flex justify-content-between"><h1>¡Hablemos!</h1><a @click="()=>{this.$bvModal.hide('modal-contact')}" style="cursor: pointer; font-size:20px"><b-icon-x-square-fill></b-icon-x-square-fill></a></b-row>
           

            <b-row class="my-2 mx-2" v-for="input in inputs" :key="input.input">

                <label 
                    class="ml-2"
                    :for="input.input">
                    {{ input.input }}:
                </label>

                <b-form-input 
                    v-if="input.input != 'Mensaje'" 
                    :id="`${input.input}`" 
                    :type="input.type"
                    v-model="input.value"
                    :class="[input.validated ? '' : 'border-pink']"
                    >
                    
                </b-form-input>

                <b-form-textarea v-else 
                    id="textarea" 
                    v-model="input.value" 
                    placeholder="Escribe tu mensaje..." 
                    rows="4"
                    :class="[input.validated ? '' : 'border-pink']"
                    max-rows="8">
                </b-form-textarea>


            </b-row>
            <b-row class="mt-4 mr-3">

                <button class="ml-auto" 
                    @click="validateForm" >
                    
                    Enviar
                </button>
            </b-row>

        </b-modal>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            inputs: [
                { 'input': 'Nombre', 'type': 'text', 'value': '', 'validated': true },
                { 'input': 'Email', 'type': 'email', 'value': '', 'validated': true },
                { 'input': 'Asunto', 'type': 'text', 'value': '', 'validated': true },
                { 'input': 'Mensaje', 'type': 'text', 'value': '', 'validated': true },
            ]
        }
    },
    methods: {
        validateForm() {
            var validated = true;
            if(this.inputs[0].value === ''){
                this.inputs[0].validated = false;
                validated = false;
            }else{
                this.inputs[0].validated = true;
            }
            if(this.inputs[1].value === ''){
                this.inputs[1].validated = false;
                validated = false;
            }else{
                this.inputs[0].validated = true;
            }
            if(this.inputs[2].value === ''){
                this.inputs[2].validated = false;
                validated = false;
            }else{
                this.inputs[0].validated = true;
            }
            if(this.inputs[3].value === ''){
                this.inputs[3].validated = false;
                validated = false;
            }else{
                this.inputs[0].validated = true;
            }
            if(validated){
                this.sendEmail();
            }else{
                this.$toast.error("Hay un error en el formulario 😱");
            }

        },
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
                this.$toast.success("Mensaje enviado con éxito 👌");
                this.$bvModal.hide('modal-contact');
            } catch (error) {
                this.$toast.error("Hubo un error al procesar tu mensaje 😭");
                console.log(error);
            }


        }
    }

}
</script>

<style lang="scss">
#modal-contact{
    .modal-body{
        border: 8px var(--sky-blue) dashed;

        background: var(--white);
        color: var(--pink);
        label{
            font-size: 20px;
        }
        input{
            color: var(--pink);
            font-size: 18px;
            &:focus{
                border-color: var(--sky-blue);
            }
        }
        textarea::placeholder{
            color: var(--pink);
        }
        button {
            border: 0px solid #fff;
            background: var(--pink);
            color: var(--white);
            font-size: clamp(16px, 32px, 40px);
            padding: 1px 12px;

            &:hover {
                box-shadow: 0 0 1px 2px var(--hover-pink) inset;
            }
        }
    }
    
    h1{
        color: var(--pink);
    }
    .border-pink{
        border-color: var(--pink);
    }
}
</style>
