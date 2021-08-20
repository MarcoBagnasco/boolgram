<template>
    <div class="stories flex jc-between">
        <Story v-for="(story, index) in stories" :key="index" :image="story.profile_picture" :name="story.profile_name"/>
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
        border: 1px solid #bbb;
        border-radius: 3px;
    }
</style>