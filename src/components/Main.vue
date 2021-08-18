<template>
    <div class="main-content container flex jc-between">
        <LeftSide/>
        <RightSide/>
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
    }
}
</script>

<style lang="scss" scoped>
    .main-content{
        height: 100vh; //fake
        padding-top: 50px;
    }
</style>