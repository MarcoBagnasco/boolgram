<template>
    <div class="story-wrap flex column jc-center ai-center">
        <!-- Image -->
        <div class="img-wrap">
            <img class="story-img" :src="image" :alt="name">
        </div>
        <!-- Name -->
        <div class="name">{{name}}</div>
    </div>
</template>

<script>

export default {
    name: 'Story',
    props:{
        image: String,
        name: String
    }
}
</script>

<style lang="scss" scoped>
.story-wrap{
    margin-top: 10px;
    width: 80px;

    .name{
        width: 100%;
        text-align: center;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
}
.img-wrap{
    margin-bottom: 10px;
    border-radius: 50%;
    border: 2px solid rgb(177, 0, 0);
}
.story-img{
    display: block;
    width: 70px;
    height: 70px;
    border-radius: 50%;
    border: 2px solid #fff;
    object-fit: cover;
}
</style>