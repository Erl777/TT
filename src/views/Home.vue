<template>
  <main>
    <section class="introduction">
      <div class="custom-container">
        <h1 class="introduction__title"> Test assignment for front-end developers </h1>
        <p class="introduction__description">
          Front-end developers make sure the user sees and interacts with all
          the necessary elements to ensure conversion. Therefore, responsive design,
          programming languages and specific frameworks are the must-have skillsets
          to look for when assessing your front-end developers.
        </p>
        <a class="yellow-btn" href="#registration">
          Sign up
        </a>
      </div>
    </section>
    <section class="custom-container acquaintance">
      <img src="/img/Image-387x340.svg" alt="">
      <div class="acquaintance__content">
        <h1 class="acquaintance__title">
          Let's get acquainted
        </h1>
        <h2 class="acquaintance__subtitle">
          I'm a good front-end developer
        </h2>
        <p class="acquaintance__description">
          What defines a good front-end developer is one that has skilled knowledge of HTML,
          CSS, JS with a vast understanding of User design thinking as they'll be building
          web interfaces with accessibility in mind. They should also be excited to learn,
          as the world of Front-End Development keeps evolving.
        </p>
        <a class="yellow-btn" href="#registration">
          Sign up
        </a>
      </div>
    </section>
    <users />
    <section id="registration" class="registration">
      <h1 class="registration__title">
        Register to get a work
      </h1>
      <h2 class="registration__subtitle">
        Your personal data is stored according to the Privacy Policy
      </h2>
      <form-register />

      <picture>
        <source media="(min-width:1400px)" class="registration__img" srcset="/img/Footprint-972x177.svg">
        <img class="registration__img" src="/img/Footprint-467x177.svg" alt="">
      </picture>
    </section>
  </main>
</template>

<script>
import formRegister from '../components/formRegister'
import users from "../components/users";

export default {
  name: 'Home',
  components: {
    formRegister, users
  },
  props: {

  }
}
</script>

<style lang="scss">
  main {
    width: 100%;
  }
  section {
    &:not(:last-child) {
      margin-bottom: 175px !important;
    }
  }
  .custom-container {
    padding: 0 60px;
    margin: 0 auto;
    max-width: 100%;
    @media (min-width: 1280px) {
      max-width: 1400px;
      padding: 0 110px;
    }
  }
  .introduction {
    height: 650px;
    background-color: #EDECEA;
    .custom-container {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      //padding-left: 60px;
      background-image: url("/img/Banner_photo.jpg");
      background-size: cover;
      background-position: center;
    }
    //margin-bottom: 175px;
    &__title {
      width: 100%;
      max-width: 670px;
      margin: 0 0 20px 0;
    }
    & &__description {
      max-width: 527px;
      margin: 0 0 25px 0;
    }
  }

  .acquaintance {
    display: flex;
    justify-content: space-between;
    text-align: right;
    //margin-bottom: 175px;
    &__content {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      padding-top: 16px;
    }
    &__title {
      margin: 0 0 10px 0;
    }
    &__subtitle {
      margin: 0 0 19px 0;
    }
    &__description {
      max-width: 477px;
      margin: 0 0 32px 0;
    }
  }

  .registration {
    position: relative;
    padding-bottom: 180px;
    &__title {
      text-align: center;
      margin: 0 0 10px 0;
    }
    &__subtitle {
      text-align: center;
      margin: 0 0 32px 0;
    }
    &__img {
      position: absolute;
      right: 0;
      bottom: 0;
      @media (min-width: 1400px) {
        right: 205px;
      }
    }
  }

</style>
