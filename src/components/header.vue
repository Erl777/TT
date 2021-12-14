<template>
  <header class="header">
    <div class="custom-container">
      <img src="img/Logo.svg" class="logo__img" alt="">
      <nav class="nav">
        <ul class="menu">
          <li v-for="item in items" class="menu__item">
            <a href="#registration" class="menu__link">{{ item }}</a>
          </li>
        </ul>
        <button class="burger" @click="$emit('openMenu')">
          <img src="img/Menu.svg">
        </button>
      </nav>
    </div>
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
    position: sticky;
    top: 0;
    left: 0;
    z-index: 1;
    height: 60px;
    background-color: #fff;
    box-shadow: -1px -1px 5px rgba(0, 0, 0, 0.15), 0px 4px 15px rgba(0, 0, 0, 0.15);

    .custom-container {
      height: 60px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 44px 0 60px;
      margin-bottom: 0;
      @media (max-width: 768px) {
        padding: 0 29px 0 32px;
      }
      @media (max-width: 500px) {
        padding: 0 24px 0 16px;
      }
    }
  }
  .menu {
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;
    list-style-type: none;
    @media (max-width: 768px) {
      display: none;
    }

    &__item {
      padding: 7px 15px;
      transition: .3s ease-in-out;
      border-radius: 4px;
      &:hover {
        background-color: #00BDD31A;
        .menu__link {
          color: #00BDD3;
        }
      }
    }
    &__link {
      text-decoration: none;
      color: #000;
      white-space: nowrap;
      transition: .3s ease-in-out;
    }
  }
  .burger {
    display: none;
    height: 24px;
    @media (max-width: 768px) {
      display: block;
    }
  }
</style>