<template>
  <div class="overlay" @click="$emit('close')">
    <div class="mobile-menu" @click.stop="">
      <div class="mobile-menu__header">
        <img src="/img/Logo.svg" class="logo__img" alt="">
      </div>
      <nav class="nav">
        <ul class="list">
          <li class="list__item">
            <a href="#registration" class="list__link"> About me </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Relationship </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Users </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Sign up </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Terms and Conditions </a>
          </li>
        </ul>
        <ul class="list">
          <li class="list__item">
            <a href="#registration" class="list__link"> How it works </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Partnership </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Help </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Level testimonial </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Contact us </a>
          </li>
        </ul>
        <ul class="list">
          <li class="list__item">
            <a href="#registration" class="list__link"> Articles </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Our news </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Testimonials </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Licenses </a>
          </li>
          <li class="list__item">
            <a href="#registration" class="list__link"> Privacy Policy </a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "mobileMenu"
}
</script>

<style scoped lang="scss">
  @mixin border-bottom {
    border: 1px solid #E0E0E0;
    margin-bottom: 30px;
  }
  .mobile-menu {
    width: 270px;
    background-color: #fff;
    &__header {
      @include border-bottom
    }
  }
  .overlay {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }
  .list {
    @include border-bottom;
    padding-bottom: 23px;
    &__item {
      padding: 7px 8px;
      transition: .3s ease-in-out;
      border-radius: 4px;
      &:hover {
        background-color: #00BDD31A;
        .list__link {
          color: #00BDD3;
        }
      }
    }
  }
</style>