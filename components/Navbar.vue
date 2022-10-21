<template>
  <section id="navbar">
    <div>
        <p class="name-tag">
            JCastilla
        </p>

    </div>
<div>
    
    <ul>
        <div class="active-bg" :style="{'top': selectorPosition}">&nbsp;</div>
        <li :class="[activeTab === 0 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Start</li>
        <li :class="[activeTab === 1 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> Work</li>
        <li :class="[activeTab === 2 ? 'active' : '']"><b-icon-record-circle-fill></b-icon-record-circle-fill> About</li>
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
       
    },
    watch:{
        activeTab(){
            if(this.activeTab === 0){
                this.selectorPosition = '0rem';
            }else if(this.activeTab ===1){
                this.selectorPosition = '65px';
            }else{
                this.selectorPosition = '130px';
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
        font-size: 55px;
        margin: 1rem 1rem;
        padding: 0px 10px;
    }

        ul {
            color: var(--white);
            font-size: 34px;
            list-style-type: none;
            margin-top: 1rem;
            padding: 0px 3rem;
            position: relative;
            .active-bg{
                background: var(--white);
                padding-left: 100px;
                position: absolute;
                width: 100%;
                z-index: -1;
            }
            li{
                font-weight: 500;
                margin: 0px 0px 1rem 1rem;
                &.active{ color: var(--pink);}
                svg{ width: 14px;}
            }
        }
    
}
</style>