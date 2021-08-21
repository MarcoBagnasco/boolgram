<template>
    <div class="posts">
        <div v-if="!wait">
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
        <!-- Seleton Loading -->
        <div v-else class="skeleton">
            <div class="title flex ai-center">
                <div class="circle"></div>
                <div class="lines">
                    <div class="line1"></div>
                    <div class="line2"></div>
                </div>
            </div>
            <div class="picture"></div>
        </div>
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
    props:{
        wait: Boolean,
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

        .skeleton{
            margin-bottom: 50px;
            border: 1px solid #ddd;
            border-radius: 3px;

            .title{
                padding: 10px 20px;

                .circle{
                    width: 40px;
                    height: 40px;
                    margin-right: 10px;
                    border-radius: 50%;
                    background-color: #ddd;
                }

                .line1,
                .line2{
                    height: 10px;
                    background-color: #ddd;
                }
                .line1{
                    width: 200px;
                }
                .line2{
                    margin-top: 5px;
                    width: 150px;
                }
            }
            .picture{
                height: 450px;
                background-color: #efefef;
            }
        }
    }
</style>