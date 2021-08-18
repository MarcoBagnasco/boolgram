<template>
    <div class="main-nav">
        <nav class="container flex jc-between ai-center">
            <div>Logo</div>
            <div>Cerca</div>
            <div class="flex">
                <div>heart</div>
                <div>home</div>
                <div>Me</div>
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
    }
</style>