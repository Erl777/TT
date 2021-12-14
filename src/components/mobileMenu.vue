<template>
  <div
          class="overlay"
          :class="{ hide: hide }"
          @click="$emit('close')"
  >
    <div class="mobile-menu" @click.stop="">
      <div class="mobile-menu__header">
        <img src="img/Logo.svg" class="logo__img" alt="">
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
  name: "mobileMenu",
  props: {
    hide: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
  @mixin border-bottom {
    border-bottom: 1px solid #E0E0E0;
    margin-bottom: 30px;
  }
  .mobile-menu {
    max-height: 100vh;
    width: 270px;
    overflow: auto;
    background-color: #fff;
    &__header {
      display: flex;
      padding: 17px 16px;
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
    z-index: 1;
    transition: transform 1s ease-in-out;
    &.hide {
      transform: translateX(-100%);
    }
  }
  .list {
    &:not(:last-child) {
      @include border-bottom;
    }
    padding-bottom: 23px;
    padding-left: 8px;
    list-style-type: none;
    &__item {
      padding: 7px 8px;
      transition: .3s ease-in-out;
      border-radius: 4px;
      &:not(:last-child) {
        margin-bottom: 8px;
      }
      &:hover {
        background-color: #00BDD31A;
        .list__link {
          color: #00BDD3;
        }
      }
    }
    &__link {
      text-decoration: none;
      color: #000;
    }
  }
</style>