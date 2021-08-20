<template>
    <div class="main-nav">
        <nav class="container flex jc-between ai-center">
            <!-- Logo -->
            <img class="logo" src="../assets/logo.png" alt="logo">

            <!-- Search -->
            <input type="text" placeholder="Cerca">

            <!-- Profile's Icons -->
            <div class="icons flex ai-center">
                <i class="far fa-heart"></i>
                <i class="fas fa-home"></i>
                <img class="profile" src="../assets/profile.jpg" alt="profile">
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    name: 'Nav',
}
</script>

<style lang="scss" scoped>
    .main-nav{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        padding: 15px;
        background-color: #fff;
        border-bottom: 1px solid #bbb;

        .logo{
            max-height: 40px;
        }

        input[type="text"]{
            appearance: none;
            width: 200px;
            padding: 8px;
            text-align: center;
            border: 1px solid #bbb;
        }

        .icons{
            font-size: 1.3rem;

            i{
                margin-right: 20px;
            }
            
            .profile{
                height: 40px;
                border-radius: 50%;
            }
        }
    }
</style>