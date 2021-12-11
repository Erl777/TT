<template>
  <section class="custom-container users">
    <h1 class="users__title">
      Our cheerful users
    </h1>
    <h2 class="users__subtitle">
      The best specialists are shown below
    </h2>
    <div class="cards">
      <div v-for="user in users"
           :key="'user' + user.id"
           class="card"
      >
        <img :src="user.photo" alt="" class="card__img" onerror="this.onerror=null;this.src='/img/Photo-cover.svg';">
        <h2 class="card__title">
          {{ user.name }}
        </h2>
        <p class="card__position">
          {{ user.position }}
        </p>
        <p class="card__email">
          {{ user.email }}
        </p>
        <p class="card__number">
          {{ user.phone }}
        </p>
      </div>
    </div>
    <button v-if="total_pages && page < total_pages" class="yellow-btn yellow-btn--center" @click="getUsers">Show more</button>
  </section>
</template>

<script>
export default {
  name: "Users",
  data() {
    return {
      users: [],
      page: 1,
      count: 9,
      total_pages: null
    }
  },
  methods: {
    getUsers(){
      this.$http
          .get(`https://frontend-test-assignment-api.abz.agency/api/v1/users?page=${this.page}&count=${this.count}`)
          .then((res) => {
            if(!this.total_pages) this.total_pages = res.data.total_pages
            this.users = [...this.users, ...res.data.users];
            this.page++
          });
    }
  },
  async created() {
    await this.getUsers();
  }
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
    }
    &__position, &__email, &__number {
      margin: 0;
      max-width: 100%;
    }
  }
</style>