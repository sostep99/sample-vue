<template>
  <div class="home">
  <div>
    <b-button v-b-toggle.collapse-1 variant="outline-primary">Create Route</b-button>
      <b-collapse id="collapse-1" class="mt-2">
        <b-card bg-variant="light" header="Information" class="text-center">
          <p class="card-text">| Timer 0:00 | Miles Long 0 | Average Speed | Target Speed |</p>
        </b-card>
    </b-collapse>

    <Gmap />
  </div>
  </div>
</template>

<script>
import Gmap from "@/components/Gmap.vue";

export default {
  components: {
    Gmap,
  }
}
</script>
