<template>
    <div class="stories">
        <div v-if="!wait" class="flex jc-between">
            <Story v-for="(story, index) in stories" :key="index" :image="story.profile_picture" :name="story.profile_name"/>
        </div>
        <!-- Skeleton Loading -->
        <div v-else class="skeleton flex jc-between ai-center">
            <div class="circle" v-for="n in 6" :key="n"></div>
            <img class="spinner" src="../assets/spinner.gif" alt="">
        </div>
    </div>
</template>

<script>
import Story from './Story.vue';
import axios from 'axios';

export default {
    name: 'StoriesBlock',
    components:{
        Story,
    },
    props:{
        wait: Boolean,
    },
    data(){
        return {
            stories: [],
        }
    },
    created(){
        this.populateStories();
    },
    methods:{
        /**
         * Populate Stories with API
         */
        populateStories(){
            axios.get('https://flynn.boolean.careers/exercises/api/boolgram/profiles')
            .then(res => {
                for(let i = 0; i < 6; i++){
                    this.stories.push(res.data[i]);
                }
            })
            .catch(err => {
                console.log(err);
            });
        },
    }
}
</script>

<style lang="scss" scoped>
    .stories{
        padding: 30px 40px;
        border: 1px solid #ddd;
        border-radius: 3px;

        .skeleton{
            position: relative;
            height: 112px;

            .circle{
                width: 70px;
                height: 70px;
                border-radius: 50%;
                background-color: #efefef;
                border: 1px solid #ddd;
            }

            .spinner{
                position: absolute;
                top: -20px;
                left: 270px;
                height: 50px;
            }
        }
    }
</style>