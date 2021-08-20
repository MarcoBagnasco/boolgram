<template>
    <div class="left">
        <StoriesBlock/>
        <PostsBlock/>
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
    }
}
</script>

<style lang="scss" scoped>
    .left{
        width: calc(60% - 50px);
        margin-right: 50px;
        // background-color: rgb(204, 122, 186);
    }
</style>