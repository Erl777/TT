<template>
  <form class="form">
    <div>
      <v-text-field
          class="form__input"
          v-for="input in inputs"
          :label="input.label"
          :placeholder="input.placeholder"
          outlined
      ></v-text-field>
    </div>
    <p class="form__subtitle">Select your position</p>
    <v-radio-group >
      <v-radio
          class="form__radio"
          v-for="radio in radios"
          :label="radio.label"
          :value="radio.label"
      ></v-radio>
    </v-radio-group>
    <v-file-input
        class="form__file-input"
        color="deep-purple accent-4"
        placeholder="Upload your photo"
        outlined
    >
    </v-file-input>
    <button class="yellow-btn yellow-btn--center disabled">Sign up</button>
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
      ],
      radios: [
        {
          label: 'Frontend developer'
        },
        {
          label: 'Backend developer'
        },
        {
          label: 'Designer'
        },
        {
          label: 'QA'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  .form {
    max-width: 380px;
    margin: 0 auto;
    &__input {
      margin-bottom: 20px !important;
      &:last-child {
        margin-bottom: 13px !important;
      }
    }
    &__subtitle {
      margin-bottom: 11px;
    }
    &__radio {
      margin-bottom: 9px !important;
      .v-input--selection-controls__input {
        left: -2px;
      }
      label {
        margin-left: 8px;
      }
    }
  }

  .v-input__slot {
    min-height: 54px !important;
  }

  .form__input .v-input__slot {
    padding: 0 15px !important;
  }

  .form__file-input .v-input__slot {
    padding-left: 99px !important;
  }

  .form .v-input--selection-controls {
    margin-top: 0;
    padding-top: 0;
    margin-bottom: 17px;
  }

  .form__file-input .v-input__prepend-outer {
    display: none;
  }

  .form__file-input .v-input__control {
    position: relative;
    &::before {
      position: absolute;
      top: 0;
      left: 0;
      content: 'Upload';
      display: flex;
      justify-content: center;
      align-items: center;
      height: 54px;
      width: 83px;
      text-align: center;
      border: 1px solid rgba(0, 0, 0, 0.87);
      box-sizing: border-box;
      border-radius: 4px 0 0 4px;
    }
  }

  .form .form__file-input {
    margin-bottom: 20px !important;
  }

</style>