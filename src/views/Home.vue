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
  </main>
</template>

<script>
export default {
  name: 'Home',
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
    margin-bottom: 175px;
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

  .yellow-btn {
    width: 148px;
    height: 50px;
    border-radius: 80px;
    background-color: #F4E041;
    font-family: 'Nunito', sans-serif;
    font-size: 16px;
    font-weight: 400;
  }
  .acquaintance {
    display: flex;
    justify-content: space-between;
    text-align: right;
    margin-bottom: 175px;
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
</style>
