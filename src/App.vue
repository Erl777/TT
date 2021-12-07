<template>
  <div id="app">
    <Header />
    <Home />
    <Footer />
  </div>
</template>

<script>
import Home from './views/Home.vue'
import Header from "./components/header";
import Footer from "./components/footer";

export default {
  name: 'App',
  components: {
    Home, Header, Footer
  }
}
</script>

<style lang="scss">
  @import "src/assets/css/styles";
</style>
