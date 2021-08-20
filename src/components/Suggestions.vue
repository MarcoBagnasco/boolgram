<template>
    <div class="suggestions">
        <div class="title flex jc-between">
            <div class="grey bold">Suggerimenti per te</div>
            <div class="bold">Mostra tutti</div>
        </div>
        <!-- People -->
        <div class="suggest flex jc-between" v-for="(person, index) in people" :key="index">
            <div class="flex ai-center">
                <img :src="person.profile_picture" :alt="person.profile_name">
                <div class="bold">{{person.profile_name}}</div>
            </div>
            <div class="link">Segui</div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Suggestions',
    data(){
        return {
            people: [],
        }
    },
    created(){
        this.populatePeople();
    },
    methods:{
        /**
         * Populate People with API
         */
        populatePeople(){
            axios.get('https://flynn.boolean.careers/exercises/api/boolgram/profiles')
            .then(res =>{
                this.people = res.data;
            })
            .catch(err =>{
                console.log(err);
            });
        }
    },
}
</script>

<style lang="scss" scoped>
    .suggestions{
        margin-top: 80px;
        background-color: rgb(255, 255, 255);

        .title{
            margin-bottom: 40px;
        }

        .suggest{
            margin-bottom: 20px;
        }

        img{
            display: block;
            height: 40px;
            width: 40px;
            object-fit: cover;
            margin-right: 20px;
            border-radius: 50%;
        }
    }
</style>