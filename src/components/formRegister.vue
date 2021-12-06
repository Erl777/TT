<template>
  <form class="form">
    <v-text-field
        class="form__input"
        v-for="input in inputs"
        :label="input.label"
        :placeholder="input.placeholder"
        outlined
    ></v-text-field>
    <v-radio-group >
      <v-radio
          v-for="n in 3"
          :key="n"
          :label="`Radio ${n}`"
          :value="n"
      ></v-radio>
    </v-radio-group>
  </form>
</template>

<script>
export default {
  name: "formRegister",
  data() {
    return {
      inputs: [
        {
          label: 'Your name',
          placeholder: 'Enter your name'
        },
        {
          label: 'Email',
          placeholder: 'Enter your email'
        },
        {
          label: 'Phone',
          placeholder: 'Enter your phone number'
        }
      ]
    }
  }
}
</script>

<style scoped lang="scss">
  .form {
    &__input {
      margin-bottom: 20px !important;
    }
  }
</style>