<template>
  <div>
    <Nav/>
    <Main/>
  </div>
</template>

<script>
import Nav from './components/Nav.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Nav,
    Main
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss';
@import '@/styles/utilities.scss';
</style>
