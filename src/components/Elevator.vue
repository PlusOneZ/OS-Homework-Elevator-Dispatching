<template>
  <div class="min-h-screen bg-cyan-200">
    <p class="sm:text-6xl font-sans py-4 text-2xl">
      In Elevator Panels
    </p>
    <div class="grid sm:grid-cols-5 grid-cols-2">
      <ElevatorPanel
          v-for="ep in this.elevNum"
          :key="'elev-'+ep"
          :floor-num="floorNum"
          :elev-name="'Elev' + ep"
          ref="elevatorList"
          @dealtDownRequest="floorDownRequestDealt"
          @dealtUpRequest="floorUpRequestDealt"
      ></ElevatorPanel>
    </div>

    <p class="sm:text-6xl font-sans py-4 text-2xl">
      Floor Panels
    </p>

    <div class="sm:grid-cols-7 grid grid-cols-2">
      <FloorPanel
          v-for="fp in this.floorNum"
          :key="'floor-' + fp"
          :current-floor="fp"
          @upRequest="floorUpRequest"
          @downRequest="floorDownRequest"
          :can-up="floorNum !== fp"
          :can-down="1 !== fp"
          ref="floorPanels"
      ></FloorPanel>
    </div>
  </div>
</template>

<script>
import '@/assets/css/tailwind.css'
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
  },

  methods: {
    floorUpRequest: function (floor) {
      var i = Math.ceil(Math.random() * 5)
      console.log("Requesting to ", i, " elevator")
      this.$refs.elevatorList[i].requestUp(floor)
    },

    floorDownRequest: function (floor) {
      var i = Math.ceil(Math.random() * 5)
      console.log("Requesting to ", i, " elevator")
      this.$refs.elevatorList[i].requestDown(floor)
    },

    floorUpRequestDealt: function (floor) {
      this.$refs.floorPanels[floor-1].upRequestHandled()
    },

    floorDownRequestDealt: function (floor) {
      this.$refs.floorPanels[floor-1].downRequestHandled()
    }
  }
}

</script>

<style scoped>

</style>