<template>
    <div class="left">
        <StoriesBlock :wait="wait"/>
        <PostsBlock :wait="wait"/>
    </div>
</template>

<script>
import StoriesBlock from './StoriesBlock.vue';
import PostsBlock from './PostsBlock.vue';

export default {
    name: 'LeftSide',
    components:{
        StoriesBlock,
        PostsBlock
    },
    props:{
        wait: Boolean,
    }
}
</script>

<style lang="scss" scoped>
    .left{
        width: calc(60% - 50px);
        margin-right: 50px;
    }
</style>