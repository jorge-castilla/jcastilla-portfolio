<template>
  <section id="hero" ref="hero">
    <div class="main-container ">
      <h1 class="animate__animated animate__fadeIn">HEY!</h1>
      <p class="animate__animated animate__fadeIn">
        SOY JORGE CASTILLA. DESARROLLADOR FULLSTACK.
      </p>

    </div>
    <!-- Button trigger modal -->

    <b-button @click="$bvModal.show('modal-contact')" @mouseover="buttonIsHovering = true"
      @mouseout="buttonIsHovering = false" :class='[buttonIsHovering ? "animate__animated animate__pulse" : ""]'>
      ¡Contáctame!</b-button>


  </section>
</template>

<script>
export default {
  data() {
    return {
      buttonIsHovering: false,
    }
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
#hero {
  background: linear-gradient(-45deg, #ff0015, var(--pink), var(--sky-blue), #1cb0eb);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  height: 100vh;

  @keyframes gradient {
    0% {
      background-position: 0% 50%;
    }

    50% {
      background-position: 100% 50%;
    }

    100% {
      background-position: 0% 50%;
    }
  }

  display: grid;
  grid-template-columns: repeat(20, 5vw);
  grid-template-rows: repeat(20, 5vh);

  .main-container {
    grid-column: 4 / 16;
    grid-row: 7 / 10;
    display: inline-flex;
    flex-direction: column;

    color: var(--white);

    h1 {
      font-size: 20vh;
      letter-spacing: 1.5rem;
      margin: 0px;

    }

    p {
      font-family: 'futura-lt';
      font-size: 3.5vh;
      letter-spacing: 2px;
      align-self: flex-start;
    }
  }

  button {
    grid-column: 15 / 19;
    grid-row: 18 / 20;
    border: 0px solid #fff;
    background: var(--white);
    color: var(--pink);
    font-size: 5vh;
    

    &:hover {
      border: 3px solid var(--pink);

    }
  }

  @media screen and (max-width: 400px) {
    .main-container {
      grid-column: 3 / 20;
      grid-row: 8 / 10;
    }

    button {
      grid-column: 10 / 19;
      grid-row: 18 / 20;
    }
  }

  @media screen and (min-width: 400px) and (max-width: 600px) {
    .main-container {
      grid-column: 3 / 20;
      grid-row: 8 / 10;

    }

    button {
      grid-column: 10 / 19;
      grid-row: 18 / 20;
    }


  }

  @media screen and (min-width: 600px) and (max-width: 768px) {
    .main-container {
      grid-column: 3 / 20;
      grid-row: 8 / 10;
    }

    button {
      grid-column: 11 / 19;
      grid-row: 18 / 20;
    }

  }

  @media screen and (min-width: 768px) and (max-width: 992px) {
    .main-container {
      grid-column: 3 / 20;
      grid-row: 8 / 10;
    }

    button {
      grid-column: 13 / 19;
      grid-row: 18 / 20;
    }

  }

  @media screen and (min-width: 992px) and (max-width: 1200px) {
    .main-container {
      grid-column: 3 / 20;
      grid-row: 8 / 10;
    }

    button {
      grid-column: 13 / 19;
      grid-row: 18 / 20;
    }
  }
}
</style>