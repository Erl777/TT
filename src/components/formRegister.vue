<template>
  <form class="form" @submit.prevent="">
    <div>
      <v-text-field
          :ref="input.value"
          class="form__input"
          v-for="input in inputs"
          v-model="formData[input.value]"
          :label="input.label"
          :placeholder="input.placeholder"
          :rules="input.rules"
          outlined
      ></v-text-field>
    </div>
    <p class="form__subtitle">Select your position</p>
    <v-radio-group
        ref="radio"
        v-model="formData.radio"
        :rules="[() => !!formData.radio || 'Choose something']"
    >
      <v-radio
          class="form__radio"
          color="primary"
          v-for="radio in radios"
          :label="radio.name"
          :value="radio.id"
      ></v-radio>
    </v-radio-group>
    <v-file-input
        ref="photo"
        v-model="formData.photo"
        class="form__file-input"
        color="deep-purple accent-4"
        placeholder="Upload your photo"
        outlined
        :rules="[() => !!formData.photo || 'Add a photo']"
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
      formData: {
        name: '',
        email: '',
        phone: '',
        radio: null,
        photo: null
      },

      inputs: [
        {
          value: 'name',
          label: 'Your name',
          placeholder: 'Enter your name',
          rules: [() => !!this.formData.name || 'This field is required']
        },
        {
          value: 'email',
          label: 'Email',
          placeholder: 'Enter your email',
          rules: [this.checkEmail]
        },
        {
          value: 'phone',
          label: 'Phone',
          placeholder: 'Enter your phone number',
          rules: [() => !!this.formData.name || 'This field is required', this.checkPhone]
        }
      ],
      radios: []
    }
  },
  computed: {
    formIsValide() {
      let formHasErrors = false

      Object.values(this.$refs).forEach(f => {
        console.log(f)
        //if (!this.formData[f]) formHasErrors = true

        //this.$refs[f].validate(true)
      })
      return formHasErrors
    }
  },
  created() {
    this.getPositions()
  },
  methods: {
    getPositions() {
      this.$http
          .get(`https://frontend-test-assignment-api.abz.agency/api/v1/positions`)
          .then((res) => {
            this.radios = Object.assign([], res.data.positions)
          });
    },
    checkEmail() {
      const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return pattern.test(this.formData.email) || 'Invalid e-mail.'
    },
    checkPhone() {
      const pattern = /^[\+]{0,1}380([0-9]{9})$/
      return pattern.test(this.formData.phone) || 'Invalid phone number.'
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