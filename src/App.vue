<template>
  <div id="app">
    <Header
      @openMenu="toggleMobileMenu"
    />
    <v-app>
      <Home />
    </v-app>
    <Footer />
    <MobileMenu
      :hide="hideMobileMenu"
      @close="toggleMobileMenu"
    />
  </div>
</template>

<script>
import Home from './views/Home.vue'
import Header from "./components/header";
import Footer from "./components/footer";
import MobileMenu from "./components/mobileMenu";

export default {
  name: 'App',
  components: {
    Home, Header, Footer, MobileMenu
  },
  data() {
    return {
      hideMobileMenu: true
    }
  },
  methods: {
    toggleMobileMenu() {
      this.hideMobileMenu = !this.hideMobileMenu
    }
  }
}
</script>

<style lang="scss">
  @import "src/assets/css/styles";
</style>
