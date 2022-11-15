<template>

    <div>
        <b-modal id="modal-contact" hide-footer hide-header>

            <b-row class="my-2 mx-2 flex justify-content-between">
                <h1>¡Hablemos!</h1><a @click="() => { this.$bvModal.hide('modal-contact') }" class="x-icon">
                    <b-icon-x-square-fill></b-icon-x-square-fill>
                </a>
            </b-row>


            <v-form lazy-validation v-model="valid" ref="form">
                <v-container class="text-center">
                    <v-text-field label="Nombre" type="Text" :min="1" :counter="20" v-model="field_1" :rules="rule_1">
                    </v-text-field>
                    <v-text-field label="Email" type="Email" :min="5" :counter="50" v-model="field_2" :rules="rule_2">
                    </v-text-field>
                    <v-text-field label="Asunto" type="Text" :min="3" :counter="25" v-model="field_3" :rules="rule_3">
                    </v-text-field>
                    <v-textarea label="Mensaje" :min="5" :counter="500" :v-model="field_4" :rules="rule_4"></v-textarea>
                    <v-btn color="accent" elevation="2" class="mt-4" @click="sendEmail">Enviar</v-btn>
                </v-container>
            </v-form>

        </b-modal>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            valid: true,
            field_1: '',
            field_2: '',
            field_3: '',
            field_4: '',
            rule_1: [v => !!v || "el nombre es requerido.", v => v.length <= 20 || "Máximo 20 caracteres",],
            rule_2: [v => !!v || "El email es requerido.", v => v.length <= 50 || "Máximo 50 caracteres", v => /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(v) || "El correo debe ser válido.",],
            rule_3: [v => !!v || "El asunto es requerido.", v => v.length <= 25 || "Máximo 25 caracteres",],
            rule_4: [v => !!v || "Un mensaje es requerido.",v => v.length <= 500 || "Máximo 500 caracteres",],
        }
    },
    methods: {

        async sendEmail() {
            if (this.$refs.form.validate()) {
                var data = {
                    service_id: 'service_ofkczni',
                    template_id: 'template_2u4jly3',
                    user_id: 'oLoYhzJdcjeEdg91w',
                    template_params: {
                        'name': this.field_1,
                        'email': this.field_2,
                        'subject': this.field_3,
                        'message': this.field_4
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

            } else {
                this.$toast.error("Existe un error de validación 🧐");
            }

        }
    }

}
</script>

<style lang="scss">
#modal-contact {
    .theme--light.v-text-field>.v-input__control>.v-input__slot:before {
        border-color: var(--pink);
    }

    .x-icon {
        cursor: pointer;
        font-size: 2vh;
        text-decoration: none;
        color: var(--pink);

        &:hover {
            color: var(--hover-pink);
        }
    }

    .modal-body {

        border: 5px var(--sky-blue) dashed;
        background: var(--white);
        color: var(--pink);

        label {
            color: var(--pink);
        }

        .v-messages__message {
            color: var(--blue);
        }

        .v-counter {
            color: var(--blue);
        }

        input {
            color: var(--blue);

            &:focus {
                border-color: var(--blue);
            }
        }

        textarea {
            color: var(--blue);
        }

        button {
            border: 0px solid #fff;
            background: var(--pink);
            color: var(--white);
            font-size: 2.5vh;
            padding: 1px 1.5em;

            &:hover {
                background: var(--hover-pink);
            }
        }
    }

    h1 {
        font-size: 4vh;
        color: var(--pink);
    }
}
</style>
