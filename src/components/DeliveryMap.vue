<template>
  <yandex-map :settings="mapSettings">
    <ymap-marker
        v-for="(c, i) in coords"
        :key="i"
        :marker-id="i"
        marker-fill="green"
        :coords="[c.lat, c.long]"
    >
    </ymap-marker>
  </yandex-map>
</template>

<script>
import { mapGetters } from 'vuex';
import { yandexMap, ymapMarker } from 'vue-yandex-maps';

export default {
  name: 'DeliveryMap',
  components: { yandexMap, ymapMarker },
  data() {
    return {
      mapSettings: {
        apiKey: '',
        lang: 'ru_RU',
        coordorder: 'latlong',
        version: '2.1',
      },
    };
  },
  computed: {
    ...mapGetters({
      coords: 'map/coords',
    }),
  },
};
</script>
