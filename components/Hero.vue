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
      grid-column: 6 / 17;
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
}

</style>