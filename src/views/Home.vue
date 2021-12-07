<template>
  <main>
    <section class="container introduction">
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
    </section>
    <section class="container acquaintance">
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
      <img class="registration__img" src="/img/Footprint-467x177.svg" alt="">
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

<style scoped lang="scss">
  header, footer, main {
    max-width: 1400px;
    margin: 0 auto;
  }
  .container {
    padding: 0 60px;
    margin-bottom: 175px;
    max-width: 100%;
  }
  .introduction {
    height: 650px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 60px;
    background-image: url("/img/Banner_photo.jpg");
    background-size: cover;
    background-position: center;
    //margin-bottom: 175px;
    &__title {
      width: 100%;
      max-width: 670px;
      margin: 0 0 20px 0;
    }
    &__description {
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
    }
  }

</style>
