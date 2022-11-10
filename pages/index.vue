<template>
    <div>
        <Modal />
        <Navbar :activeSection=activeSection @scrollTo="scrollToSection" />
        <Hero />
        <Work />
        <About />
    </div>
</template>

<script>
import 'animate.css';
export default {
    name: "IndexPage",
    data() {
        return {
            activeSection: 0,
            inMove: false,
            inMoveDelay: 400,
            offsets: [],
            touchStartY: 0,
        }
    },
    mounted() {
    }

}

</script>

<style lang="scss">
section{
    width: 100%;
}

</style>