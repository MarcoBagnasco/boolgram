<template>
    <div class="stories flex jc-between">
        <Story v-for="n in 6" :key="n"/>
    </div>
</template>

<script>
import Story from './Story.vue';

export default {
    name: 'StoriesBlock',
    components:{
        Story,
    }
}
</script>

<style lang="scss" scoped>
    .stories{
        padding: 30px 40px;
        background-color: rgb(93, 21, 209);
        border: 1px solid #bbb;
    }
</style>