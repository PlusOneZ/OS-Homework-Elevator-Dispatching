<template>
  <div class="">
    <p class="text-6xl font-sans py-4">
      In Elevator Panels
    </p>
    <div class="grid grid-cols-5">
      <ElevatorPanel
          v-for="ep in this.elevNum"
          :key="'elev-'+ep"
          :floor-num="floorNum"
          :elev-name="'Elev' + ep"
          :current-floor="1"
          :going-down="false"
          :going-up="false"
      ></ElevatorPanel>
    </div>

    <p class="text-6xl font-sans py-4">
      Floor Panels
    </p>

    <div class="grid-cols-7 grid">
      <FloorPanel
          v-for="fp in this.floorNum"
          :key="'floor-' + fp"
          :current-floor="fp"
      ></FloorPanel>
    </div>
  </div>
</template>

<script>
import ElevatorPanel from "@/components/ElevatorPanel";
import FloorPanel from "@/components/FloorPanel";

export default {
  name: "Elevator",
  components: {ElevatorPanel, FloorPanel},
  props: {},
  data() {
    return {
      elevNum: 5,
      floorNum: 20,
    }
  }
}

</script>

<style scoped>

</style>