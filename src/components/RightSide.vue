<template>
    <div class="right">
        <Profile/>
        <Suggestions/>
        <RightFooter/>
    </div>
</template>

<script>
import Profile from './Profile.vue';
import Suggestions from './Suggestions.vue';
import RightFooter from './RightFooter.vue';

export default {
    name: 'RightSide',
    components:{
        Profile,
        Suggestions,
        RightFooter
    }    
}
</script>

<style lang="scss" scoped>
    .right{
        width: 40%;
        background-color: rgb(134, 216, 132);
    }
</style>