<template>
    <section class="custom-container users">
        <h1 class="users__title">
            Our cheerful users
        </h1>
        <h2 class="users__subtitle">
            The best specialists are shown below
        </h2>
        <Loader v-if="loading" />
        <template v-else >
            <div class="cards">
                <div v-for="user in users"
                     class="card"
                >
                    <img :src="user.photo" alt="" class="card__img"
                         onerror="this.onerror=null;this.src='/img/Photo-cover.svg';">
                    <h2 class="card__title">
                        {{ user.name }}
                    </h2>
                    <p class="card__position">
                        {{ user.position }}
                    </p>
                    <v-tooltip bottom content-class="tooltip" nudge-right="50%">
                        <template v-slot:activator="{ on, attrs }">
                            <a v-bind="attrs"
                               v-on="on" class="card__email" :href='"mailto:" + user.email'>{{ user.email }}</a>
                        </template>
                        <span>{{ user.email }}</span>
                    </v-tooltip>
                    <a :href='"tel:" + user.phone ' class="card__number"> {{ user.phone }} </a>
                </div>
            </div>
            <slot name="afterCards" />

        </template>
    </section>
</template>

<script>
  import Loader from "./preloader";

  export default {
    name: "Users",
    components: {
      Loader
    },
    props: {
      users: {
        type: Array,
        required: true,
      },
      loading: {
        type: Boolean,
        required: true
      }
    },
  }
</script>

<style scoped lang="scss">
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
        grid-template-columns: repeat(3, minmax(282px, 370px));
        grid-template-rows: repeat(auto-fill, 313px);
        margin-bottom: 50px;
        @media (min-width: 1024px) {
            grid-gap: 30px;
        }
        @media (max-width: 992px) {
            grid-template-columns: repeat(2, minmax(282px, 1fr));
            grid-gap: 16px;
        }
        @media (max-width: 768px) {
            grid-template-columns: repeat(2, minmax(282px, 344px));
            grid-gap: 16px;
        }
        @media (max-width: 650px) {
            grid-template-columns: repeat(1, minmax(282px, 1fr));
            grid-gap: 20px;
        }
    }

    .card {
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
        color: #000;

        &__img {
            min-height: 70px;
            min-width: 70px;
            border-radius: 50%;
            margin-bottom: 15px;
        }

        &__title {
            margin: 0 0 4px 0;
            max-height: 56px;
            max-width: 100%;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        &__position {
            max-height: 52px;
            max-width: 100%;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        &__email {
            max-height: 26px;
            max-width: 100%;
            overflow: hidden;
            text-overflow: ellipsis;
            color: #000;
            text-decoration: none;
        }

        &__number {
            color: #000;
            text-decoration: none;
        }

        &__position, &__email, &__number {
            margin: 0;
            max-width: 100%;
        }
    }
    .tooltip {
        background-color: #232F34;
        border-radius: 4px;
    }
</style>