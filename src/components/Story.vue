<template>
    <div class="story-wrap">
        <div class="img-wrap">
            <img class="story-img" src="../assets/landscape.png" alt="story">
        </div>
        <div>ciao</div>
    </div>
</template>

<script>

export default {
    name: 'Story',
}
</script>

<style lang="scss" scoped>
.story-wrap{
    margin-top: 10px;
    text-align: center;
}
.img-wrap{
    margin-bottom: 10px;
    border-radius: 50%;
    border: 2px solid #f00;
}
.story-img{
    display: block;
    width: 70px;
    height: 70px;
    border-radius: 50%;
    border: 3px solid #fff;
    object-fit: cover;
}
</style>