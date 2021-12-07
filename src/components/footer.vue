<template>
  <footer class="footer">
    <div class="footer__content">
      <span>© abz.agency specially for the test task</span>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer"
}
</script>

<style scoped lang="scss">
  .footer {
    &__content {
       display: flex;
       align-items: center;
       justify-content: center;
       height: 57px;
       background-color: #fff;
       text-align: center;
     }
  }
</style>