<template>
  <section id="hero" ref="hero">
    <div class="main-container">
      <h1>HELLO;</h1> 
      <p>
        I'M JORGE CASTILLA. FULLSTACK DEVELOPER. 
      </p>

    </div>
    <button @click="scrollToAbout">Contact me!</button>

    
  </section>
</template>

<script>
export default {
  methods:{
    scrollToAbout(){
            window.scrollTo(0, 2*window.innerHeight);
            // to begin of contact section, typable
        }
  }
}
</script>

<style lang="scss" scoped>
#hero{
    background-color: var(--sky-blue);
    height: 100vh;
    width: 100%;
    display: grid;
    grid-template-columns: repeat(20, 5vw);
    grid-template-rows: repeat(20, 5vh);
    .main-container{
      grid-column: 4 / 16;
      grid-row: 7 / 10;
      display: inline-flex;
      flex-direction: column;

      color: var(--white);
      h1{
        font-size: 175px;
        letter-spacing: 1.5rem;
        margin: 0px;
      }
      p{
        font-family: 'futura-lt';
        font-size: 2.4rem;
        letter-spacing: 2px;
        align-self: flex-start;
      }
    }
    button{
      grid-column: 15 / 19;
      grid-row: 18 / 20;
      border: 0px solid #fff;
      background: var(--white);
      color: var(--pink);
      font-size: 44px;
      &:hover{
        border: 3px solid var(--pink);
        
      }
    }
    @media screen and (max-width: 400px) {
      .main-container{
        grid-column: 3 / 20;
        grid-row: 8 / 10;
        h1{
          letter-spacing: 1rem;
          font-size: 55px !important;
        }
        p{

        font-size: 25px;

      }
      }
      button{
        grid-column: 10 / 19;
        grid-row: 18 / 20;
        font-size: 29px !important;
      }
    }
    @media screen and (min-width: 400px) and (max-width: 600px) {
      .main-container{
        grid-column: 3 / 20;
        grid-row: 8 / 10;
        h1{
          letter-spacing: 1rem;
          font-size: 75px !important;
        }
        p{

        font-size: 25px;

      }
      }
      button{
        grid-column: 10 / 19;
        grid-row: 18 / 20;
        font-size: 32px !important;
      }
    

    }

    @media screen and (min-width: 600px) and (max-width: 768px) {
      .main-container{
        grid-column: 3 / 20;
        grid-row: 8 / 10;
        h1{
          letter-spacing: 1rem;
          font-size: 100px !important;
        }
        p{

        font-size: 35px;

      }
      }
      button{
        grid-column: 11 / 19;
        grid-row: 18 / 20;
        font-size: 45px !important;
      }
    
    }
    @media screen and (min-width: 768px) and (max-width: 992px) {
      .main-container{
        grid-column: 3 / 20;
        grid-row: 8 / 10;
        h1{
          letter-spacing: 1rem;
          font-size: 115px !important;
        }
        p{

        font-size: 38px;

      }
      }
      button{
        grid-column: 13 / 19;
        grid-row: 18 / 20;
        font-size: 45px !important;
      }

    }
    @media screen and (min-width: 992px) and (max-width: 1200px) {
      .main-container{
        grid-column: 3 / 20;
        grid-row: 8 / 10;
        h1{
          letter-spacing: 1rem;
          font-size: 130px !important;
        }
        p{

        font-size: 40px;

      }
      }
      button{
        grid-column: 13 / 19;
        grid-row: 18 / 20;
        font-size: 45px !important;
      }
    }
}

</style>