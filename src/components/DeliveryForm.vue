<template>
  <b-container fluid>
    <b-row class="">
      <b-col md="6">
        <b-form-group
            label="ФИО"
            label-for="input-name"
        >
          <b-form-input
              id="input-name"
              v-model="name"
              :state="nameState"
              trim
              placeholder="Только кириллица"
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
          ></b-form-input>
        </b-form-group>
      </b-col>
      <b-col md="6">
        <b-form-group
            label="Телефон"
            label-for="input-phone"
        >
          <b-form-input
              id="input-phone"
              v-model="phone"
              trim
              v-mask="'+7 (###) ###-##-##'"
              placeholder="+7 (___) ___-__-__"
          ></b-form-input>
        </b-form-group>
      </b-col>
      <b-col md="6">
        <b-form-group
            label="Адрес доставки"
            label-for="input-address"
        >
          <b-form-input
              id="input-address"
              v-model="address"
              trim
              placeholder="Город, улица, дом"
          >

          </b-form-input>
        </b-form-group>
      </b-col>
      <b-col md="6">
        <b-form-group
            label="Комментарии"
            label-for="input-comments"
        >
          <b-form-textarea
              id="input-comments"
              v-model="comments"
              trim
          >
          </b-form-textarea>
        </b-form-group>
      </b-col>
      <b-col md="12" class="text-right">
        <b-button @click="save">Отправить</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import { validationMixin } from 'vuelidate';

const { required } = require('vuelidate/lib/validators');

const cyrillicOnly = (value) => /^[а-яА-ЯЁё ]*$/.test(value);

export default {
  name: 'DeliveryForm',
  mixins: [validationMixin],
  validations: {
    name: {
      required,
      cyrillicOnly,
    },
  },
  data() {
    return {
      name: '',
      phone: '',
      address: '',
      comments: '',
    };
  },
  computed: {
    nameState() {
      return this.$v.name.$dirty ? !this.$v.name.$error : null;
    },
  },
  methods: {
    save() {
      this.$v.$touch();
    },
  },
};
</script>

<style lang="scss">
label.d-block {
  text-align: left;
}
</style>
