<template>
    <div class="suggestions">
        <div class="title flex jc-between">
            <div class="grey bold">Suggerimenti per te</div>
            <div class="bold">Mostra tutti</div>
        </div>
        <!-- People -->
        <div v-if="!wait" >
            <div class="suggest flex jc-between" v-for="(person, index) in people" :key="index">
                <div class="flex ai-center">
                    <img :src="person.profile_picture" :alt="person.profile_name">
                    <div class="bold">{{person.profile_name}}</div>
                </div>
                <div class="link">Segui</div>
            </div>
        </div>
        <!-- Skeleton Loading -->
        <div v-else>
            <div class="suggest flex ai-center" v-for="n in 8" :key="n">
                <div class="circle"></div>
                <div class="loading">
                    <div class="line1"></div>
                    <div class="line2"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Suggestions',
    props:{
        wait: Boolean,
    },
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

        .circle{
            width: 40px;
            height: 40px;
            margin-right: 10px;
            border-radius: 50%;
            background-color: #efefef;
            border: 1px solid #ddd;
        }

        .line1,
        .line2{
            height: 10px;
            background-color: #efefef;
        }
        .line1{
            width: 120px;
        }
        .line2{
            margin-top: 5px;
            width: 70px;
        }

        .loading{
            &::after{
                width: 350%;
                height: 350%;
            }
        }
    }
</style>