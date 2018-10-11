<template>
 <div id="trips">
  <div v-for="(trip, index) in trips" :key="trip.id">
   <p>{{trip.name}} is my {{trip.description}}</p>
  </div>
 </div>
</template>

<script>
import axios from 'axios'
export default {
 data() {
  return {
   trips: [],
   name: [],
   description: [],
   errors: []
  }
 },
 created() {
  axios.get('http://localhost:3000/v1/trips')
  .then(response => {
   this.trips = response.data
  })
 .catch(e => {
  this.errors.push(e)
  })
 },
}
</script>

<style>
</style>
