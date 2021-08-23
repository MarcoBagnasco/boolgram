<template>
    <div class="main-content container flex jc-between">
        <LeftSide :wait="wait"/>
        <RightSide :wait="wait"/>
    </div>
</template>

<script>
import LeftSide from './LeftSide.vue';
import RightSide from './RightSide.vue';
export default {
    name: 'Main',
    components:{
        LeftSide,
        RightSide
    },
    data(){
        return{
            wait: true,
        }
    },
    created(){
        this.makeWait();
    },
    methods:{
        /**
         * Simulate wait
         */
        makeWait(){
            setTimeout(() => {
                this.wait = false;
            }, 4000);
        }
    }
}
</script>

<style lang="scss" scoped>
    .main-content{
        padding-top: 50px;
    }
</style>