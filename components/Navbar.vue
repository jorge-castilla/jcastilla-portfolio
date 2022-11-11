<template>
  <nav id="navbar">
    <div>
        <p class="name-tag">
            JCastilla
        </p>

    </div>

  </nav>
</template>

<script>
export default {
    props:{
    },
    data(){
        return{

        }
    },
    watch:{

    }

}
</script>

<style lang="scss" scoped>
#navbar{
    display: flex;
    justify-content: space-between;
    position: fixed;
    width: 100%;
    z-index: 10;
    .name-tag{
        background: var(--pink);
        color: var(--white);
        font-size: 6vh;
        margin: 0.3em 0.3em;
        padding: 0px 0.2em;
        transform: scale(1, 1.1);
        cursor: pointer;
        &:hover{
            background: var(--hover-pink);
        }
    }
        ul {
            color: var(--white);
            font-family: 'futura-md';
            font-size: 24px;
            list-style-type: none;
            margin-top: 1rem;
            padding: 0px 3rem;
            position: relative;
            .active-bg{
                background: var(--white);
                padding-left: 100px;
                position: absolute;
                width: 100%;
                transition: 0.2s;
                z-index: -1;
            }
            li{
                cursor: pointer;
                font-weight: 500;
                margin: 0px 0px 1rem 1rem;
                &.active{ color: var(--pink);}
                svg{ width: 14px;}
                transition: 0.2s;
            }
        }}
</style>