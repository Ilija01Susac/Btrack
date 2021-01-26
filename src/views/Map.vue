<template>
  <div class="map">
    <h1>Čapljina-Mostar(8:30)</h1>
      <GoogleMap
  api-key="AIzaSyBzIgJXoF2aCKNf_ri6DLgOw_bJ9dK0I0M"
  style="width: 100%; height: 600px"
  :center="{ lat: lat, lng: lng }"
  :zoom="25"
  :scrollwheel=false
  :draggable="false"
  >
    <Marker :options="{ position: { lat: lat, lng: lng } }" />
  </GoogleMap>
  </div>
</template>

<script>
import db from '../components/firebaseInit'
import { GoogleMap, Marker } from 'vue3-google-map'

export default {
  name: 'Map',
  components: { GoogleMap, Marker },
  data () {
      return {
            id: null,
            lat: null,
            lng: null
      }
    },
  created () {
      db.collection('buses').onSnapshot((snapshotChange) => {
        snapshotChange.forEach((doc) => {
          console.log(doc.data());
          this.id = doc.data().id;
          this.lat = doc.data().lat;
          this.lng = doc.data().lng;
        })
      });
      
    }
}


</script>

<style scoped>
    #map {
      height: 100%;
    }
    html,
    body {
      height: 100%;
      margin: 0;
      padding: 0;
    }
</style>
