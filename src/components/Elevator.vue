
<template>
<div class="grid grid-cols-5">
  <ElevatorPanel
      v-for="ep in this.elevNum"
      :key="'elev-'+ep"
      :floor-num="floorNum"
      :elev-name="'Elev' + ep"
      :current-floor="1"
      > </ElevatorPanel>
</div>

</template>

<script>
import ElevatorPanel from "@/components/ElevatorPanel";

export default {
  name: "Elevator",
  components: {ElevatorPanel},
  props: {
  },
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