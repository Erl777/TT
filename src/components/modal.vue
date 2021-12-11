<template>
  <div class="overlay" @click="$emit('close')">
    <div class="modal" @click.stop="">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal"
}
</script>

<style scoped lang="scss">
  .overlay {
    position: fixed;
    left: 0;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1;
  }
  .modal {
    width: 452px;
    background-color: #fff;
    border-radius: 4px;
    padding: 24px;
    &__title {
      line-height: 31px;
      margin-bottom: 6px;
    }
    &__description {
      margin-bottom: 33px;
    }
    .yellow-btn {
      margin-left: auto;
    }
  }
</style>