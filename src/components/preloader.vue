<template>
    <div class="loader-container">
        <v-progress-circular
                indeterminate
                color="#00BDD3"
                :size="48"
        ></v-progress-circular>
    </div>
</template>

<script>
  export default {
    name: "preloader"
  }
</script>

<style scoped>
    .loader-container {
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>