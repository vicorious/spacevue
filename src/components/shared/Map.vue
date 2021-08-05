

<template>
<div style="margin: 0 auto">
<div>
  <vue-google-maps
    style="width: 1200px; height: 300px"
    :map-config="mapConfig"
    :api-key="apiKey"
  ></vue-google-maps>
</div>
</div>
</template>

<script>
import VueGoogleMaps from "@point-hub/vue-google-maps";

export default {
  components: {
    VueGoogleMaps
  },
  data() {
    return {
      apiKey: "AIzaSyDHxiSs1OzdWqeDGGkV5LdJTDbbf0-K58Q",
      mapConfig: {
        zoom: 16,
        center: {
          lat: -7,
          lng: 112
        }
      }
    };
  }
};
</script>