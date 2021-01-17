<template>
  <div class="bus">
    <h1>{{ id }}</h1>
      <GoogleMap
  api-key="AIzaSyBzIgJXoF2aCKNf_ri6DLgOw_bJ9dK0I0M"
  style="width: 100%; height: 500px"
  :center="center"
  :zoom="15"
  >
    <Marker :options="{ position: center }" />
  </GoogleMap>
  </div>
</template>

<script>
import db from './firebaseInit'
import { GoogleMap, Marker } from 'vue3-google-map'

export default {
  name: 'Bus',
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
      
    },
    setup() {
    const center = { lat: this.lat, lng: this.lng }
    return { center }
  },
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
