<template>
  <div>
    <b-container>
      <h1>Выберите способ доставки</h1>
      <b-tabs content-class="tab-content">
        <b-tab title="Доставка" active>
          <delivery-form></delivery-form>
        </b-tab>
        <b-tab title="Самовывоз">

        </b-tab>
      </b-tabs>
    </b-container>
  </div>
</template>

<script>

import DeliveryForm from '../components/DeliveryForm.vue';

export default {
  name: 'Home',
  components: {
    DeliveryForm,
  },
};
</script>

<style lang="scss">
  h1 {
    color: #222;
    text-align: left;
    margin: 20px 0;
    font-size: 27px;
  }
  .tab-content {
    padding: 1.5rem;
    border-radius: 3px;
    background: #FFF;
  }
</style>
