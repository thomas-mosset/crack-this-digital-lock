<template>
  <div class="wrapper">
    <Header />
    <CrackPWD />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import CrackPWD from './components/CrackPWD.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    CrackPWD,
    Footer,
  },
};
</script>

<style lang="scss">
@import './scss/reset.scss';

#app {
  font-family: 'Inconsolata', monospace;
  background-color: #FBFBFB;
  min-height: 100vh;
}

.wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
