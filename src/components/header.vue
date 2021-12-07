<template>
  <header class="header">
    <img src="/img/Logo.svg" class="logo__img" alt="">
    <nav class="nav">
      <ul class="menu">
        <li v-for="item in items" class="menu__item">
          <a href="#registration" class="menu__link">{{ item }}</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      items: ['About me', 'Relationships', 'Requirements', 'Users', 'Sign Up']
    }
  }
}
</script>

<style scoped lang="scss">
  .header {
  //position: sticky;
  //top: 0;
  //left: 0;
  //z-index: 1;
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
   }
  }
</style>