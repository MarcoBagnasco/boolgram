<template>
    <div class="post">
        <!-- Profile -->
        <div class="profile flex flex jc-between ai-center">
            <div class="flex ai-center">
                <div class="img-wrap">
                    <img class="img-profile" :src="imgProfile" :alt="name">
                </div>
                <div class="bold">{{fullName}}</div>
            </div>
            <i class="fas fa-ellipsis-h"></i>
        </div>

        <!-- Post Image -->
        <img class="img-post" :src="imgPost" alt="post image"> 

        <!-- Caption -->
        <div class="caption">
            <!-- Icons -->
            <div class="icons flex">
                <i class="far fa-heart"></i>
                <i class="far fa-comment"></i>
            </div>
            <!-- Likes -->
            <div class="likes flex ai-center">
                <img class="img-likes" :src="likes[0].profile_picture" :alt="likes[0].username">
                <div>Piace a <span class="bold">{{likes[0].username}}</span> e <span class="bold">{{likes.length - 1}} altri</span></div>
            </div>
            <!-- Post Text -->
            <div class="post-text"><span class="bold">{{name}}</span> {{text}}</div>
            <!-- Comments -->
            <div class="comments">
                <div class="show-comments grey" @click="toggle">Mostra tutti e {{comments.length}} commenti</div>
                <div v-if="!show">
                    <div v-for="(comment, index) in comments" :key="index">
                        <div v-if="index < 3"><span class="bold">{{comment.username}}</span> {{comment.text}}</div>
                    </div>
                </div>
                <div v-else>
                    <div v-for="(comment, index) in comments" :key="index">
                        <span class="bold">{{comment.username}}</span> {{comment.text}}
                    </div>
                </div>
            </div>
            <!-- Time -->
            <div class="time grey">{{time}}</div>
            <!-- My Comment -->
            <div class="my-comment flex jc-between ai-center">
                <input type="text" placeholder="Aggiungi un commento" v-model="myComment.text"  @keyup.enter="publish">
                <div class="link" @click="publish">Pubblica</div>
            </div>
        </div>
    </div>
</template>

<script>
import dayjs from 'dayjs';
import 'dayjs/locale/it';
        dayjs.locale('it');
        dayjs.extend(require('dayjs/plugin/relativeTime'));
        
export default {
    name: 'Post',
    props: {
        imgProfile: String,
        name: String,
        fullName: String,
        imgPost: String,
        likes: Array,
        text: String,
        comments: Array,
        date: Object,
    },
    data(){
        return{
            myComment: {
                username: 'Marco.B',
                text: '',
            },
            show: false,
            time: '',
        }
    },
    created(){
        this.time = dayjs().to(dayjs(this.date.date));
    },
    methods: {
        /**
         * Toggle all comments visibility
         */
        toggle(){
            this.show = !this.show;
        },

        /**
         * Publish my comment
         */
        publish(){
            const comm = {...this.myComment};
            this.comments.unshift(comm);
            this.myComment.text = '';
        }
    }
}
</script>

<style lang="scss" scoped>
.post{
    margin-bottom: 50px;
    border: 1px solid #bbb;
    border-radius: 3px;
    overflow: hidden;

    .profile{
        padding: 10px 20px;
    }
    .img-wrap{
        margin-right: 20px;
        border-radius: 50%;
        border: 2px solid rgb(177, 0, 0);
    }
    .img-profile{
        display: block;
        width: 35px;
        height: 35px;
        border-radius: 50%;
        border: 2px solid #fff;
        object-fit: cover;
    }

    .img-post{
        width: 670px;
        // height: auto;
    }

    .caption{
        padding-top: 20px;
        
        .icons{
            margin-bottom: 20px;
            padding-left: 20px;
            font-size: 1.7rem;
    
            i{
                margin-right: 20px;
            }
        }

        .likes{
            margin-bottom: 15px;
            padding-left: 20px;

            .img-likes{
                display: block;
                width: 25px;
                height: 25px;
                margin-right: 10px;
                border-radius: 50%;
                object-fit: cover;                
            }
        }

        .post-text{
            margin-bottom: 20px;
            padding-left: 20px;
        }

        .comments{
            margin-bottom: 30px;
            padding-left: 20px;

            .show-comments{
                cursor: pointer;
            }

            div{
                margin-top: 5px;
            }
        }

        .time{
            margin-bottom: 20px;
            padding-left: 20px;
        }

        .my-comment{
            padding: 20px;
            border-top: 1px solid #bbb;
            input{
                font-size: 1.2rem;
                border: 0;
                outline: none;
            }
        }
    }
}

</style>