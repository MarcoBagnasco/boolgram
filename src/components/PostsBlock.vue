<template>
    <div class="posts">
        <Post v-for="n in 3" :key="n"/>
    </div>
</template>

<script>
import Post from './Post.vue';

export default {
    name: 'PostsBlock',
    components:{
        Post,
    }
}
</script>

<style lang="scss" scoped>
    .posts{
        height: 100vh;//fake
        margin-top: 50px;
        background-color: rgb(255, 153, 0);
    }
</style>