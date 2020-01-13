<template>
  <div class="home">
  <div>
      <!-- This button contains a dropdown with place holder stats for the currunt route your doing. -->

    <b-form-input v-model="origin.lat" placeholder="Enter the origin latitude"></b-form-input>
    <b-form-input v-model="origin.long" placeholder="Enter the origin longitude"></b-form-input>
    <b-form-input v-model="destination.lat" placeholder="Enter the destination latitude"></b-form-input>
    <b-form-input v-model="destination.long" placeholder="Enter the destination longitude"></b-form-input>


    <b-button v-b-toggle.collapse-1 variant="outline-primary" v-on:click="route()">Create Route</b-button>
      <b-collapse id="collapse-1" class="mt-2">
        <b-card bg-variant="light" header="Information" class="text-center">
          <p class="card-text">| Timer 0:00 | Miles Long 0 | Average Speed | Target Speed |</p>
        </b-card>
    </b-collapse>
      <!-- This puts the Gmap on this page and keeps it loaded when at other pages -->

    <keep-alive>
      <Gmap ref="map"/>
    </keep-alive>
  </div>
  </div>
</template>

<script>
// Brings the Map to this page
import Gmap from "@/components/Gmap.vue";

export default {
  components: {
    Gmap,
  },
  data: function () {
    return {
      message: "hello",
      origin: {
        lat: 41.850033,
        long:-87.6500523
      },
      destination: {
        lat: 45.07067,
        long: -103.01291
      }
    }
  },
  methods: {
    route: function () {
      console.log(this.message);
      let origin = {
        lat: null,
        long: null
      }
      origin.lat = this.origin.lat;
      origin.long = this.origin.long;
      
      let destination = {
        lat: null,
        long: null
      }
      destination.lat = this.destination.lat;
      destination.long = this.destination.long;
      this.$refs["map"].calcRoute(origin, destination);
    }
  }
}
</script>
