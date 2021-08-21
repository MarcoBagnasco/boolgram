<template>
    <div class="posts">
        <Post v-for="(post, index) in posts" :key="index" 
            :imgProfile="post.profile_picture"
            :name="post.profile_name"
            :fullName="post.profile_fullname"
            :imgPost="post.post_image"
            :likes="post.likes"
            :text="post.post_text"
            :comments="post.comments"
            :date="post.date"
            />
    </div>
</template>

<script>
import Post from './Post.vue';
import axios from 'axios';

export default {
    name: 'PostsBlock',
    components:{
        Post,
    },
    data(){
        return {
            posts: [],
        }
    },
    created(){
        this.populatePosts();
    },
    methods:{
        populatePosts(){
            axios.get('https://flynn.boolean.careers/exercises/api/boolgram/posts')
            .then(res => {
                this.posts = res.data;
            })
            .catch(err => {
                console.log(err);
            });
        }
    },
}
</script>

<style lang="scss" scoped>
    .posts{
        margin-top: 50px;
    }
</style>