<template>
    <section id="about" ref="about">

        <div class="main-container">

            <div class="image-container">
                <div id="portrait">

                </div>
                <div class="stack-button">
                    <div class="stack" v-if="windowWidth >= 600">
                        <img src="../assets/icons/javascript_logo.png" alt="Javascript">
                        <img src="../assets/icons/php_logo.png" alt="PHP">
                        <img src="../assets/icons/vue_logo.png" alt="Vue">
                        <img src="../assets/icons/laravel_logo.png" alt="Laravel">
                        <img src="../assets/icons/node_logo.png" alt="Node">
                        <img src="../assets/icons/bootstrap_logo.png" alt="Bootstrap">
                    </div>
                    <b-button v-if="windowWidth < 768" @click="$bvModal.show('modal-contact')">¡Háblame!</b-button>
                </div>
            </div>

            <div>

                <div>
                    <h1 @click="() => {
                        if (!showWho && windowWidth <= 600) {
                            showWho = !showWho
                            showWhat = false
                        }
                    }
                    ">
                        <b-icon-arrow-right></b-icon-arrow-right>¿Quien soy?
                    </h1>


                    <p v-if="showWho">Soy un desarrollador web fullstack radicado en Chile. Me gusta analizar el mundo
                        que nos rodea
                        desde
                        todos los puntos de vista posibles, aprendiendo lo más posible de las personas y desafíos que
                        encuentro
                        en mi camino.
                        Si no me encuentro desarrollando un proyecto, estoy creando música o leyendo sobre algo
                        interesante.
                    </p>

                </div>
                <div>
                    <h1 @click="() => {
                        if (!showWhat && windowWidth <= 600) {
                            showWhat = !showWhat
                            showWho = false
                        }
                    }">
                        <b-icon-arrow-right class="right-arrow"></b-icon-arrow-right>¿Qué puedo hacer?
                    </h1>

                    <p v-if="showWhat">Soy capaz de convertir problemas dificiles en soluciones simples y eficientes,
                        proponiendo
                        alternativas basadas en mis conocimientos y capacidades analíticas. Estoy siempre dispuesto a
                        mejorar y ofrecer mi ayuda e interés en los proyectos de los que formo parte.
                    </p>



                </div>
            </div>
        </div>
        <div class="btn-container">
            <b-button v-if="windowWidth >= 768" @click="$bvModal.show('modal-contact')">¡Háblame!</b-button>
        </div>


    </section>
</template>
  
<script>
export default {
    data() {
        return {
            windowHeight: window.innerHeight,
            windowWidth: window.innerWidth,
            showWho: true,
            showWhat: true,
        }
    },
    mounted() {
        if (this.windowWidth <= 600) {
            this.showWhat = false;
        }
        this.$nextTick(() => {
            window.addEventListener('resize', this.onResize);
        })
    },
    beforeDestroy() {
        window.removeEventListener('resize', this.onResize);
    },

    methods: {
        onResize() {
            this.windowHeight = window.innerHeight
            this.windowWidth = window.innerWidth
            if (this.windowWidth <= 600) {
                this.showWho = true;
                this.showWhat = false;
            } else {
                this.showWhat = true;
            }
        }
    },
}
</script>
  
<style lang="scss">
#about {
    background-color: var(--dark-blue);
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;

    .main-container {
        color: var(--white);
        margin: 0px auto 0px auto;
        background: var(--sky-blue);
        border: 12px dashed var(--pink);
        display: grid;
        grid-template-columns: 25vw 50vw;
        gap: 20px;
        min-height: 70vh;
        max-height: 90vh;
        width: min-content;

        .stack {
            display: flex;
            align-items: center;
            justify-content: space-around;
            background: var(--white);
            color: var(--pink);
            border: 2px var(--pink) solid;
            flex-wrap: wrap;
            padding: 10px;
            font-size: 32px;
            margin: 5px 0px 0px 0px;
            width: 360px;

            img {
                width: 48px;
                max-width: 100%;

                &:hover {
                    opacity: 0.5;
                }
            }
        }

        h1 {
            font-size: 50px;
            background: var(--pink);
        }


        p {
            border: 2px var(--white) solid;
            font-size: 30px;
            text-align: center;
            padding: 20px;
            margin-bottom: 1px;
            // min-height: auto;

            &:hover {

                border: 2px var(--white) dashed;
            }
        }


        div {
            max-width: 100%;
            margin: 12px;
        }

        .image-container {
            height: 100%;
            width: 100%;
            margin-top: 0px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;

            #portrait {
                border: 4px var(--pink) solid;
                position: relative;
                display: block;
                width: 360px;
                height: 580px;
                background: linear-gradient(to top, #0d8abc60, #ff008c36), url('../assets/images/portrait.png') no-repeat center;
                background-size: cover;
                resize: both;
                transition: 1s;

                &:hover {
                    border: 4px var(--pink) dashed;
                }

                &:after {
                    content: '';
                    position: absolute;
                    left: 0px;
                    top: 0px;
                    right: 0px;
                    bottom: 0px;
                    background: url('../assets/images/portrait.png') no-repeat center;
                    background-size: cover;
                    resize: both;
                    opacity: 0;
                    transition: all 1s ease-in-out;
                }

                &:hover:after {
                    opacity: 1;

                }

            }
        }
    }

    .btn-container {
        display: flex;
        justify-content: center;
        margin: 0px;

        button {
            border: 0px solid #fff;
            background: var(--white);
            color: var(--pink);
            font-size: 44px;
            padding: 10px 70px;

            &:hover {
                box-shadow: 0 0 1px 2px var(--pink) inset;
            }
        }

    }

    @media screen and (min-width: 320px) and (max-width: 420px) {
        .main-container {

            margin: 30px 0px 0px 12px;
            grid-template-columns: 75vw;
            grid-template-rows: repeat(3, 1fr);
            gap: 0px;

            div {
                margin: 1px 2px;
            }

            .image-container {
                padding-top: 12px;
                flex-direction: column;
                gap: 0px;

                #portrait {
                    max-width: 150px;
                    max-height: 150px;
                }

                button {
                    border: 0px solid #fff;
                    background: var(--white);
                    color: var(--pink);
                    font-size: 22px;
                    min-width: 150px;
                    padding: 5px 10px;
                    box-shadow: 0 0 1px 2px var(--pink) inset;
                }

                .stack-button {
                    display: flex;
                    flex-direction: column;
                    justify-content: center;

                    .stack {
                        margin: 0px;
                        width: 100px;
                        max-width: 180px;
                        gap: 5px;

                    }

                    img {
                        width: 20px;
                    }

                }

            }

            h1 {
                font-size: 28px;
            }

            p {
                font-size: 16px;
                padding: 10px;
                text-align: justify;
                text-justify: inter-word;
            }
        }
    }

    @media screen and (min-width: 420px) and (max-width: 600px) {

        .main-container {

            margin: 30px 0px 0px 12px;
            grid-template-columns: 75vw;
            grid-template-rows: repeat(3, 1fr);
            gap: 0px;

            .image-container {
                padding-top: 12px;
                flex-direction: row;

                #portrait {
                    max-width: 150px;
                    max-height: 150px;
                }

                button {
                    border: 0px solid #fff;
                    background: var(--white);
                    color: var(--pink);
                    font-size: 22px;
                    min-width: fit-content;
                    padding: 5px 10px;
                    box-shadow: 0 0 1px 2px var(--pink) inset;
                }

                .stack-button {
                    display: flex;
                    flex-direction: column;
                    justify-content: center;

                    .stack {
                        margin: 0px;
                        width: 100px;
                        max-width: 180px;
                        gap: 5px;

                    }

                    img {
                        width: 20px;
                    }

                }

            }

            h1 {
                font-size: 32px;
            }

            p {
                font-size: 16px;
                text-align: justify;
                text-justify: inter-word;
            }
        }


    }


    @media screen and (min-width: 600px) and (max-width: 768px) {
        .main-container {
            margin: 30px 0px 0px 12px;

            .image-container {
                justify-content: center;
                padding-top: 55px;

                #portrait {
                    width: 150px;
                    height: 240px;
                }

                button {
                    border: 0px solid #fff;
                    background: var(--white);
                    color: var(--pink);
                    font-size: 25px;
                    width: 150px;
                    padding: 5px 20px;
                    box-shadow: 0 0 1px 2px var(--pink) inset;
                }

                .stack {
                    margin: 0px;
                    width: 150px;
                    gap: 5px;

                }

                img {
                    width: 20px;
                }
            }

            h1 {
                font-size: 30px;
            }

            p {
                font-size: 16px;
            }
        }

        .btn-container {
            button {
                font-size: 33px;
                padding: 10px 55px;

            }
        }
    }


    @media screen and (min-width: 768px) and (max-width: 1024px) {
        .main-container {
            margin: 30px 0px 0px 12px;

            .image-container {
                #portrait {
                    width: 200px;
                    height: 321px;
                }
            }

            .stack {
                width: 200px;
                gap: 5px;

                img {
                    width: 32px;
                }
            }

            h1 {
                font-size: 35px;
            }

            p {
                font-size: 20px;
            }
        }

        .btn-container {
            button {
                font-size: 33px;
                padding: 10px 55px;

            }
        }

    }

    @media screen and (min-width: 1024px) and (max-width: 1366px) {
        .main-container {
            .image-container {
                #portrait {
                    width: 250px;
                    height: 402px;
                }
            }

            .stack {
                width: 250px;

                img {
                    width: 32px;
                }
            }

            h1 {
                font-size: 40px;
            }

            p {
                font-size: 22px;
            }
        }

        .btn-container {
            button {
                font-size: 36px;
                padding: 10px 60px;

            }
        }


    }

    @media screen and (min-width: 1367px) and (max-width: 1500px) {
        .main-container {
            .image-container {
                #portrait {
                    width: 300px;
                    height: 483px;
                }
            }

            .stack {
                width: 300px;

                img {
                    width: 32px;
                }
            }

            h1 {
                font-size: 43px;
            }

            p {
                font-size: 25px;
            }
        }

        .btn-container {
            button {
                font-size: 38px;
                padding: 7px 65px;

            }
        }
    }
}


// width: min-content;
</style>