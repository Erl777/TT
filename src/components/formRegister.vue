<template>
  <form class="form" @submit.prevent="">
    <div>
      <v-text-field
          class="form__input"
          v-model="name"
          label="Your name"
          placeholder="Enter your name"
          :error-messages="nameErrors"
          outlined
          color="#00BDD3"
          @blur="$v.name.$touch()"
      ></v-text-field>
      <v-text-field
              class="form__input"
              v-model="email"
              label="Email"
              placeholder="Enter your email"
              validate-on-blur
              :error-messages="emailErrors"
              outlined
              color="#00BDD3"
              @blur="$v.email.$touch()"
      ></v-text-field>
      <v-text-field
              class="form__input"
              v-model="phone"
              label="Phone"
              placeholder="Enter your phone number"
              validate-on-blur
              :error-messages="phoneErrors"
              outlined
              color="#00BDD3"
              @blur="$v.phone.$touch()"
      ></v-text-field>
    </div>
    <p class="form__subtitle">Select your position</p>
    <v-radio-group
        v-model="position"
    >
      <v-radio
          class="form__radio"
          v-for="radio in radios"
          :label="radio.name"
          :value="radio.id"
          color="#00BDD3"
      ></v-radio>
    </v-radio-group>
    <v-file-input
        v-model="photo"
        class="form__file-input"
        placeholder="Upload your photo"
        outlined
        color="#000"
        :error-messages="photoErrors"
        @blur="$v.photo.$touch()"
    >
    </v-file-input>
    <button
        class="yellow-btn yellow-btn--center "
        :class="{ disabled: formInvalid }"
        @click="createUser"
    >
      Sign up
    </button>
    <Modal
        v-if="success"
        @close="success = false"
    >
      <slot>
        <h2 class="modal__title">
          Congratulations
        </h2>
        <p class="modal__description">
          You have successfully passed the registration
        </p>
        <button
            class="yellow-btn"
            @click="success = false"
        >
          Great
        </button>
      </slot>
    </Modal>
  </form>
</template>

<script>
const phoneValidation = (value) => /^[\+]{0,1}380([0-9]{9})$/.test(value)
const { validationMixin, default: Vuelidate } = require('vuelidate')
const { required, maxLength, email, minLength } = require('vuelidate/lib/validators')
import Modal from "./modal";
export default {
  name: "formRegister",
  mixins: [validationMixin],
  components: { Modal },
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      position: null,
      photo: null,
      radios: [],
      success: false
    }
  },
  validations: {
    name: { required, maxLength: maxLength(60), minLength: minLength(2) },
    email: { required, email },
    phone: { required, phoneValidation },
    position: { required },
    photo: { required },
  },
  computed: {
    formInvalid() {
      return this.$v.$invalid
    },
    nameErrors () {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength && errors.push('Name must be at most 60 characters long')
      !this.$v.name.minLength && errors.push('Name must be more than 2 characters long')
      !this.$v.name.required && errors.push('Name is required.')
      return errors
    },
    emailErrors () {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push('Must be valid e-mail')
      !this.$v.email.required && errors.push('E-mail is required')
      return errors
    },
    phoneErrors () {
      const errors = []
      if (!this.$v.phone.$dirty) return errors
      !this.$v.phone.required && errors.push('E-mail is required')
      !this.$v.phone.phoneValidation && errors.push('Must be valid phone number start with +380')
      return errors
    },
    photoErrors () {
      const errors = []
      if (!this.$v.photo.$dirty) return errors
      !this.$v.photo.required && errors.push('Photo is required')
      return errors
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
    async createUser() {
      const token = await this.getToken();
      const config = {
          headers: {
            Token: token
          }
        };
      let payload = new FormData();
      payload.append('position_id', this.position);
      payload.append('name', this.name);
      payload.append('email', this.email);
      payload.append('phone', this.phone);
      payload.append('photo', this.photo);
      this.$http
          .post(`https://frontend-test-assignment-api.abz.agency/api/v1/users`, payload, config)
          .then((res) => {
            this.success = true;
            this.clearForm();
            this.$emit('refreshUsers')
          }).catch((err) => {
            throw new Error(err)
          });

    },
    clearForm() {
      this.$v.$reset();
      this.name = '';
      this.email = '';
      this.phone = '';
      this.position = null;
      this.photo = null;
    },
    getToken(){
      return this.$http
          .get(`https://frontend-test-assignment-api.abz.agency/api/v1/token`)
          .then((res) => {
            return res.data.token
          });
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
    & &__subtitle {
      margin-bottom: 11px;
    }
    &__radio {
      margin-bottom: 9px !important;
      .v-input--selection-controls__input {
        left: -2px;
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
      color: #000;
    }
  }

  .form .form__file-input {
    margin-bottom: 20px !important;
    &.error--text {
      .v-input__control {
        &::before {
          border: 2px solid #ff5252;
        }
      }
    }
  }

</style>