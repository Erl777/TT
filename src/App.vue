<template>
  <div id="app">
    <header class="header">
      <img src="/img/Logo.svg" class="logo__img" alt="">
      <nav class="nav">
        <ul class="menu">
          <li class="menu__item">
            <a href="#" class="menu__link">About me</a>
          </li>
          <li class="menu__item">
            <a href="#" class="menu__link">Relationships</a>
          </li>
          <li class="menu__item">
            <a href="#" class="menu__link">Requirements</a>
          </li>
          <li class="menu__item">
            <a href="#" class="menu__link">Users</a>
          </li>
          <li class="menu__item">
            <a href="#" class="menu__link">Sign Up</a>
          </li>
        </ul>
      </nav>
    </header>
    <Home />
    <footer class="footer">
      <div class="footer__content">
        <span>© abz.agency specially for the test task</span>
      </div>
      <div class="footer__underline">

      </div>
    </footer>
  </div>
</template>

<script>
import Home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style lang="scss">
  @import "src/assets/css/styles";
  .header {
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #fff;
    padding: 0 60px;
    box-shadow: -1px -1px 5px rgba(0, 0, 0, 0.15), 0px 4px 15px rgba(0, 0, 0, 0.15);
  }
  .nav {
    width: 53.65%;
  }
  .menu {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0;
    padding: 0;
    list-style-type: none;
    &__item:not(:last-child) {
      margin-right: 30px;
    }
    &__link {
      text-decoration: none;
      color: #000;
      white-space: nowrap;
      // 489
    }
  }
  .footer {
    display: none;
    &__content {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 57px;
      background-color: #fff;
      text-align: center;
    }
    &__underline {
      height: 40px;
      background-color: #000;
    }
  }
</style>
