<template>
    <main>
        <section class="introduction">
            <div class="custom-container">
                <h1 class="introduction__title"> Test assignment for front-end developers </h1>
                <p class="introduction__description">
                    {{ `Front-end developers make sure the user sees and interacts with all
                    the necessary elements to ensure conversion. Therefore, responsive design,
                    programming languages and specific frameworks are the must-have skillsets
                    to look for when assessing your front-end developers.` | crop(window.width)}}
                </p>
                <a class="yellow-btn" href="#registration">
                    Sign up
                </a>
            </div>
        </section>
        <section class="custom-container acquaintance">
            <picture>
                <source media="(max-width:768px)" class="acquaintance__img" srcset="/img/Image-296x260.svg">
                <img class="acquaintance__img" src="/img/Image-387x340.svg" alt="">
            </picture>
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
                <a class="acquaintance__btn yellow-btn" href="#registration">
                    Sign up
                </a>
            </div>
        </section>
        <users
            :users="users"
            :loading="loading"
        >
            <template v-slot:afterCards>
                <button v-if="total_pages && page < total_pages" class="yellow-btn yellow-btn--center"
                        @click="getUsers">Show
                    more
                </button>
            </template>
        </users>
        <section id="registration" class="registration">
            <h1 class="registration__title">
                Register to get a work
            </h1>
            <h2 class="registration__subtitle">
                Your personal data is stored according to the Privacy Policy
            </h2>
            <form-register @refreshUsers="refreshUsers"/>

            <picture>
                <source media="(min-width:1400px)" class="registration__img" srcset="/img/Footprint-972x177.svg">
                <source media="(max-width:500px)" class="registration__img" srcset="/img/Footprint-328x124.svg">
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
    data() {
      return {
        window: {
          width: 0,
          height: 0
        },
        users: [],
        page: 1,
        count: 9,
        total_pages: null,
        loading: true
      }
    },
    async created() {
      window.addEventListener('resize', this.handleResize);
      this.handleResize();
      await this.getUsers();
    },
    destroyed() {
      window.removeEventListener('resize', this.handleResize);
    },
    methods: {
      handleResize() {
        this.window.width = window.innerWidth;
        this.window.height = window.innerHeight;
        if(this.window.width <= 768) this.count = 6;
        if(this.window.width <= 400) this.count = 3;
      },
      getUsers() {
        this.$http
          .get(`https://frontend-test-assignment-api.abz.agency/api/v1/users?page=${this.page}&count=${this.count}`)
          .then((res) => {
            if (!this.total_pages) this.total_pages = res.data.total_pages
            this.users = [...this.users, ...res.data.users];
            this.page++;
            this.loading = false;
          });
      },
      refreshUsers() {
        this.loading = true;
        this.page = 1;
        this.users = Object.assign([], []);
        this.getUsers()
      }
    },
    filters: {
      crop: (str, width) => {
        if (width <= 650) {
          return str.split('.')[0] + '.'
        } else {
          return str
        }
      }
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
            @media (max-width: 650px) {
                margin-bottom: 145px !important;
            }
            @media (min-width: 2500px) {
                margin-bottom: 185px !important;
            }
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
        @media (max-width: 992px) {
            padding: 0 32px;
        }
        @media (max-width: 650px) {
            padding: 0 16px;
        }
    }

    .introduction {
        height: 650px;
        background-color: #EDECEA;
        @media (max-width: 768px) {
            height: 500px;
        }
        @media (max-width: 360px) {
            height: 470px;
        }

        .custom-container {
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            background-image: url("/img/Banner_photo.jpg");
            background-size: cover;
            background-position: center;
            @media (min-width: 760px) and (max-width: 768px) {
                background-position-x: -140px;
            }
        }

        &__title {
            width: 100%;
            max-width: 670px;
            margin: 0 0 20px 0;
            @media (max-width: 768px) {
                max-width: 410px;
                margin-bottom: 21px;
            }
            @media (max-width: 650px) {
                max-width: 240px;
            }
        }

        & &__description {
            max-width: 527px;
            margin: 0 0 25px 0;
            @media (max-width: 768px) {
                max-width: 424px;
                margin-bottom: 32px;
            }
            @media (max-width: 650px) {
                max-width: 240px;
            }

        }
    }

    .acquaintance {
        display: flex;
        justify-content: space-between;
        text-align: right;
        @media (max-width: 650px) {
            flex-direction: column;
            align-items: center;
            text-align: left;
        }

        &__content {
            padding-top: 16px;
            @media (max-width: 768px) {
                padding-top: 0;
            }
        }

        &__title {
            margin: 0 0 10px 0;
        }

        &__subtitle {
            margin: 0 0 19px 0;
        }
        picture {
          max-height: 340px;
        }
        &__img {
            @media (max-width: 768px) {
                margin-top: 50px;
            }
            @media (max-width: 650px) {
                margin: 0 0 40px 0;
            }
        }

        & &__description {
            max-width: 477px;
            margin: 0 0 32px 0;
            @media (min-width: 1400px) {
                max-width: 680px;
            }
            @media (max-width: 768px) {
                max-width: 368px;
            }
        }

        &__btn {
            margin-left: auto;
            @media (max-width: 650px) {
                margin: 0 auto 0 0;
            }
        }
    }

    .registration {
        position: relative;
        padding-bottom: 180px;
        @media (max-width: 400px) {
            padding: 0 16px 150px;
        }

        &__title {
            text-align: center;
            margin: 0 0 10px 0;
        }

        &__subtitle {
            text-align: center;
            margin: 0 0 30px 0;
            @media (max-width: 768px) {
                margin-bottom: 32px;
            }
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
