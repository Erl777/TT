<template>
  <main>
    <section class="container introduction">
      <h1 class="main-title"> Test assignment for front-end developers </h1>
      <p class="introduction__description">
        Front-end developers make sure the user sees and interacts with all
        the necessary elements to ensure conversion. Therefore, responsive design,
        programming languages and specific frameworks are the must-have skillsets
        to look for when assessing your front-end developers.
      </p>
      <button class="yellow-btn">Sign up</button>
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
  .introduction {
    height: 650px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 60px;
    background-image: url("/img/Banner_photo.jpg");
    background-size: cover;
    background-position: center;
    &__description {
      max-width: 527px;
      margin: 0 0 25px 0;
    }
  }
  .main-title {
    width: 100%;
    max-width: 670px;
    margin: 0 0 20px 0;
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
</style>
