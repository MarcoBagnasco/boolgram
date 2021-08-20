<template>
    <div class="profile flex jc-between ai-center">
        <!-- Profile Image -->
        <img class="img-profile" src="../assets/profile.jpg" alt="profile">
        <!-- Profile Name -->
        <div>
            <div class="name bold">marcobagnasco</div>
            <div class="grey">Marco Bagnasco</div>
        </div>
        <!-- Link -->
        <div class="link">Passa a</div>
    </div>
</template>

<script>
export default {
    name: 'Profile',
}
</script>

<style lang="scss" scoped>
    .profile{        
        .img-profile{
            height: 60px;
            border-radius: 50%;
        }

        .name{
            margin-bottom: 5px;
        }
    }
</style>