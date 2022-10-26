<template>
    <section id="about" ref="about">

        <div class="main-container">

            <div class="image-container">
                <img src="../assets/images/portrait.png" id="portrait" alt="Jorge Castilla">
                <div class="stack">
                    <img src="../assets/icons/javascript_logo.png" alt="Javascript">
                    <img src="../assets/icons/php_logo.png" alt="PHP">
                    <img src="../assets/icons/vue_logo.png" alt="Vue">
                    <img src="../assets/icons/laravel_logo.png" alt="Laravel">
                    <img src="../assets/icons/node_logo.png" alt="Node">
                    <img src="../assets/icons/bootstrap_logo.png" alt="Bootstrap">
                </div>
                <button v-if="windowWidth < 768">¡Háblame!</button>
            </div>

            <div>

                <div>
                    <h1>
                        <b-icon-arrow-right></b-icon-arrow-right>¿Quien soy?
                    </h1>


                    <p>Soy un desarrollador web fullstack radicado en Chile. Me gusta analizar el mundo que nos rodea
                        desde
                        todos los puntos de vista posibles, aprendiendo lo más posible de las personas y desafíos que
                        encuentro
                        en mi camino.
                        Si no me encuentro desarrollando un proyecto, estoy creando música o leyendo sobre algo
                        interesante.
                    </p>

                </div>
                <div>
                    <h1>
                        <b-icon-arrow-right class="right-arrow"></b-icon-arrow-right>¿Qué puedo hacer?
                    </h1>

                    <p>Soy capaz de convertir problemas dificiles en soluciones simples y eficientes, proponiendo
                        alternativas basadas en mis conocimientos y capacidades analíticas. Estoy siempre dispuesto a
                        mejorar y ofrecer mi ayuda e interés en los proyectos de los que formo parte.
                    </p>



                </div>
            </div>
        </div>
        <div class="btn-container">
            <button v-if="windowWidth >= 768">¡Háblame!</button>
        </div>


    </section>
</template>
  
<script>
export default {
    data() {
        return {
            windowHeight: window.innerHeight,
            windowWidth: window.innerWidth,
        }
    },
    mounted() {
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
                width: 360px;
                height: 580px;

                &:hover {}

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

    @media screen and (max-width: 400px) {}

    @media screen and (min-width: 400px) and (max-width: 600px) {}

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