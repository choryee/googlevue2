/* eslint-disable */ 

<script>
import { computed } from 'vue';
import { useGeolocation } from './useGeolocation';


export default {
  name: 'App',
  setup(){
    const {coords}=useGeolocation()
    const currPos=computed(()=>({
      lat:coords.value.latitude,
      lng:coords.value.longitude
    }))
    return {currPos}

  }
  
}

</script>

<template>
  <div class="d-flex text-center" style="height:20vh">
    <div class="m-auto">
      <h4>Your position</h4>
      Latitude:{{ currPos.lat.toFixed(2) }}, Longitude: {{ currPos.lng.toFixed(2) }}
    </div>
  </div>
</template>
