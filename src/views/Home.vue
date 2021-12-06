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
      <button class="yellow-btn">Sign up</button>
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
        <button class="yellow-btn">Sign up</button>
      </div>
    </section>
    <section class="container users">
      <h1 class="users__title">
        Our cheerful users
      </h1>
      <h2 class="users__subtitle">
        The best specialists are shown below
      </h2>
      <div class="cards">
        <div class="card">
          <img src="/img/Photo-cover.svg" alt="" class="card__img">
          <h2 class="card__title">
            Salvador Stewart Flynn Thomas Salva...
          </h2>
          <p class="card__position">
            Leading specialist of the department of control over
          </p>
          <p class="card__email">
            JeromeKlarkaJeromeKlarka@...
          </p>
          <p class="card__number">
            +38 (098) 278 76 24
          </p>
        </div>
        <div class="card"></div>
        <div class="card"></div>
        <div class="card">
          <img src="/img/Photo-cover.svg" alt="" class="card__img">
          <h2 class="card__title">
            Alexandre
          </h2>
          <p class="card__position">
            Lead Independent Director
          </p>
          <p class="card__email">
            Alexandr_develop@gmail.com
          </p>
          <p class="card__number">
            +38 (098) 198 44 24
          </p>
        </div>
        <div class="card"></div>
        <div class="card"></div>
        <div class="card">
          <img src="/img/Photo-cover.svg" alt="" class="card__img">
          <h2 class="card__title">
            Oliver
          </h2>
          <p class="card__position">
            VP, Global IT Operations
          </p>
          <p class="card__email">
            Oliver_develop@gmail.com
          </p>
          <p class="card__number">
            +38 (098) 039 44 87
          </p>
        </div>
        <div class="card"></div>
        <div class="card"></div>
      </div>
      <button class="yellow-btn yellow-btn--center">Show more</button>
    </section>
    <section class="feedback">
      <h1 class="feedback__title">
        Register to get a work
      </h1>
      <h2 class="feedback__subtitle">
        Your personal data is stored according to the Privacy Policy
      </h2>
      <form-register />
      <img class="feedback__img" src="/img/Footprint-467x177.svg" alt="">
    </section>
  </main>
</template>

<script>
import formRegister from '../components/formRegister'

export default {
  name: 'Home',
  components: {
    formRegister
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

  .users {
    &__title {
      text-align: center;
      margin: 0 0 10px 0;
    }
    &__subtitle {
      text-align: center;
      margin: 0 0 32px 0;
    }
  }

  .cards {
    display: grid;
    grid-gap: 29px;
    grid-template-columns: repeat(3, 282px);
    grid-template-rows: repeat(auto-fill, 313px);
    margin-bottom: 50px;
  }

  .card {
    max-width: 282px;
    height: 313px;
    max-height: 313px;
    display: flex;
    flex-direction: column;
    padding: 36px 30px 0;
    align-items: center;
    background: #FFFFFF;
    border-radius: 10px;
    text-align: center;
    box-sizing: border-box;
    &__img {
      border-radius: 50%;
      margin-bottom: 15px;
    }
    &__title {
      margin: 0 0 4px 0;
    }
    &__position, &__email, &__number {
      margin: 0;
    }
  }

  .feedback {
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
