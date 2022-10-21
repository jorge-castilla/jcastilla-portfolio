<template>
  <section id="navbar">
    <div>
        <p class="name-tag" @click='scrollTo(0)'>
            JCastilla
        </p>

    </div>
<div>
    
    <ul>
        <div class="active-bg" :style="{'top': selectorPosition}">&nbsp;</div>
        <li @click='scrollTo(0)' :class="[activeTab === 0 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Start</li>
        <li @click='scrollTo(1)' :class="[activeTab === 1 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Work</li>
        <li @click='scrollTo(2)' :class="[activeTab === 2 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> About</li>
    </ul>
</div>

  </section>
</template>

<script>
export default {
    props:{
        activeTab: Number,
    },
    data(){
        return{
            selectorPosition: '0rem',
        }
    },
    methods:{
        scrollTo(mult){
            window.scrollTo(0, mult*window.innerHeight);
        }
       
    },
    watch:{
        activeTab(){
            if(this.activeTab === 0){
                this.selectorPosition = '0rem';
            }else if(this.activeTab ===1){
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
    
}
</style>