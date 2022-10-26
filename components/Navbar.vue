<template>
  <nav id="navbar">
    <div>
        <p class="name-tag" @click="$emit('scrollTo', 0)">
            JCastilla
        </p>

    </div>
<div>
    
    <ul>
        <div class="active-bg" :style="{'top': selectorPosition}">&nbsp;</div>
        <li @click="$emit('scrollTo', 0)" :class="[activeSection === 0 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Start</li>
        <li @click="$emit('scrollTo', 1)" :class="[activeSection === 1 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Work</li>
        <li @click="$emit('scrollTo', 2)" :class="[activeSection === 2 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> About</li>
    </ul>
</div>

  </nav>
</template>

<script>
export default {
    props:{
        activeSection: Number,
    },
    data(){
        return{
            selectorPosition: '0rem',
        }
    },
    watch:{
        activeSection(){
            if(this.activeSection === 0){
                this.selectorPosition = '0rem';
            }else if(this.activeSection ===1){
                this.selectorPosition = '51px';
            }else{
                this.selectorPosition = '102px';
            }

        },
    }

}
</script>

<style lang="scss" scoped>
#navbar{
    display: flex;
    height: 5vh;
    justify-content: space-between;
    position: fixed;
    width: 100%;
    .name-tag{
        background: var(--pink);
        color: var(--white);
        font-size: 3.5rem;
        margin: 1rem 1rem;
        padding: 0px 10px;
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
        }
        @media screen and (min-width: 1px) and (max-width: 600px) {
            .name-tag{
                font-size: 2.5rem;
            }
            ul{
                padding: 0px 1rem;
                li{
                    font-size: 20px;
                    margin-bottom: 1.4rem;
                }
            }
        }
        @media screen and (max-width: 400px) {

}
@media screen and (min-width: 400px) and (max-width: 600px) {

}
@media screen and (min-width: 600px) and (max-width: 768px) {
    .name-tag{
        font-size: 2.5rem;
    }
    
}
@media screen and (min-width: 768px) and (max-width: 992px) {
    .name-tag{
        font-size: 2.8rem;
    }
    
}
@media screen and (min-width: 992px) and (max-width: 1200px) {
    .name-tag{
        font-size: 3rem;
    }

}
    
}
</style>