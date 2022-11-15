<template>
    <section id="about" ref="about" class="d-flex justify-content-center align-items-center">

        <div class="main-container m-5 d-flex flex-wrap justify-content-around">

            <div class="img-container d-flex flex-column align-items-center justify-content-center">
                <img src='../assets/images/portrait.png' alt="Jorge Castilla" class="my-2 mx-5" id="portrait">

                <div class="stack p-2 mt-2 d-flex align-items-center justify-content-center">
                    <img src="../assets/icons/javascript_logo.png" alt="Javascript">
                    <img src="../assets/icons/php_logo.png" alt="PHP">
                    <img src="../assets/icons/vue_logo.png" alt="Vue">
                    <img src="../assets/icons/laravel_logo.png" alt="Laravel">
                    <img src="../assets/icons/node_logo.png" alt="Node">
                </div>
            </div>
            <div class="d-flex flex-column justify-content-center align-items-center">

                <div class="py-2">
                    <h1>
                        <b-icon-arrow-right></b-icon-arrow-right>¿Quien soy?
                    </h1>
                    <p>
                        Soy un desarrollador web fullstack radicado en Chile. Me gusta analizar el mundo
                        que nos rodea
                        desde
                        todos los puntos de vista posibles, aprendiendo cuanto pueda de las personas y desafíos que
                        encuentro
                        en mi camino.
                        Si no me encuentro desarrollando un proyecto, estoy creando música o leyendo sobre algo
                        interesante.
                    </p>
                </div>
                <div class="py-2">
                    <h1>
                        <b-icon-arrow-right class="right-arrow"></b-icon-arrow-right>¿Qué puedo hacer?
                    </h1>
                    <p>
                        Soy capaz de convertir problemas dificiles en soluciones simples y eficientes,
                        proponiendo
                        alternativas basadas en mis conocimientos y capacidades analíticas. Estoy siempre dispuesto a
                        mejorar y ofrecer mi ayuda e interés en los proyectos de los que formo parte.
                    </p>
                </div>
                <div class="btn-container d-flex align-items-center justify-content-center flex-wrap">

                    <b-button @click="$bvModal.show('modal-contact')" class="my-2 about-btn">¡Háblame!</b-button>
                    <a href="Curriculum Vitae Jorge Castilla.pdf" download>
                        <b-icon-file-earmark-text-fill class="about-icon"></b-icon-file-earmark-text-fill>
                    </a>
                    <a href="https://github.com/jorge-castilla" target="_blank">
                        <b-icon-github class="about-icon"></b-icon-github>
                    </a>
                </div>
            </div>
        </div>


    </section>
</template>
  
<script>
export default {
    data() {
        return {
        }
    },
}
</script>
  
<style lang="scss">
#portrait {
    width: 35vmin;
    max-width: 350px;
    border: 2px var(--pink) solid;
    position: relative;
}

#about {
    background-color: var(--dark-blue);
    min-height: 100vh;

    .about-icon {
        text-decoration: none;
        font-size: 4vh;
        color: var(--white);
        transition: 450ms;

        &:hover {
            color: var(--pink);
        }

        margin: 1em 0.5em 1em 0.5em;
    }

    .about-btn {
        margin: 0px 0.5em 0px 0.5em;
    }

    .main-container {
        color: var(--white);
        background: var(--sky-blue);
        border: 12px dashed var(--dark-blue);
        max-width: 90vw;
        grid-auto-flow: column;
        padding: 4vmin;

        .stack {
            background: var(--white);
            color: var(--pink);
            border: 2px var(--pink) solid;
            width: fit-content;

            img {
                width: 3.5vh;
                margin: 0px 0.2em 0px 0.2em;

                &:hover {
                    opacity: 0.5;
                }
            }
        }

        h1 {
            font-size: 5vh;
            background: var(--pink);
            max-width: 700px;
        }


        p {
            border: 2px var(--white) solid;
            font-size: 2.5vh;
            padding: 20px;
            text-align: justify;
            max-width: 700px;
            // min-height: auto;

            &:hover {
                border: 2px var(--white) dashed;
            }
        }
    }



    button {
        border: 0px solid #fff;
        background: var(--white);
        color: var(--pink);
        font-size: 4vh;
        padding: 0.3em 2em;

        &:hover {
            box-shadow: 0 0 1px 2px var(--pink) inset;
        }
    }



}


// width: min-content;
</style>