<template>
  <div>
    <Navbar :activeTab=activeTab />
    <Hero />
    <Work />
    <About />
  </div>
</template>

<script>

export default {
  name: "IndexPage",
  data() {
    return {
      activeTab: 0,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.checkScrollPosition);
  },
  methods: {
    checkScrollPosition() {
      if(window.scrollY >= window.innerHeight && window.scrollY < (2* window.innerHeight)){
        this.activeTab = 1;
        console.log('im at second tab');
      }else if(window.scrollY >= (2* window.innerHeight)){
        this.activeTab = 2;
        console.log('im at third tab');
      }else{
        this.activeTab = 0;
        console.log('im at first tab');
      }
    },
    scrollOnePage(){
    }
  },
  watch: {

  }

}

</script>
