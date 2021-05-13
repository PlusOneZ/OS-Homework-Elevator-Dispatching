<template>
  <div class="min-h-screen bg-blue-200">
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

    <div class="sm:grid-cols-6 grid grid-cols-2">
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

let UP = 1
let DOWN = 2

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
      let i = this.findElevatorToDeal(floor, UP)
      console.log("Requesting to ", i, " elevator")
      this.$refs.elevatorList[i].requestUp(floor)
    },

    floorDownRequest: function (floor) {
      let i = this.findElevatorToDeal(floor, DOWN)
      console.log("Requesting to ", i, " elevator")
      this.$refs.elevatorList[i].requestDown(floor)
    },

    floorUpRequestDealt: function (floor) {
      this.$refs.floorPanels[floor-1].upRequestHandled()
    },

    floorDownRequestDealt: function (floor) {
      this.$refs.floorPanels[floor-1].downRequestHandled()
    },

  //   findElevatorToDeal: function (floor, direction) {
  //     var score = [0, 0, 0, 0, 0]
  //     console.log("haha",score)
  //     for (let i in this.elevNum) {
  //       let elevator = this.$refs.elevatorList[i]
  //       score[i] = Math.abs(floor - elevator.currentFloor)
  //       if (elevator.goingUp && direction === UP) {
  //         score += 0
  //       } else if (elevator.goingDown && direction === DOWN) {
  //         score += 0
  //       } else {
  //         score += 10
  //       }
  //     }
  //
  //     var minIndex = 0
  //     for (let j = 1; j < this.elevNum; j++) {
  //       if (score[j] < score[minIndex]) minIndex = j
  //     }
  //
  //     return minIndex
  //   },
  //
  //   }
  // }

    findElevatorToDeal: function (floor, direction) {
      var dispatchedTo = -1
      var distance = this.floorNum + 1
      var inTrailDistance = this.floorNum + 1
      for (var i = 0; i < this.elevNum; i++) {
        let elevator = this.$refs.elevatorList[i]
        if (direction === UP) {
          if (elevator.goingUp && elevator.currentFloor <= floor) {
            if (elevator.currentFloor === floor) return i
            if (elevator.maxInQueue > floor) {
              if (floor - elevator.currentFloor < inTrailDistance) {
                inTrailDistance = floor - elevator.currentFloor
                dispatchedTo = i
              }
            } else {
              if (inTrailDistance === this.floorNum + 1 && floor - elevator.currentFloor < distance) {
                distance = elevator.currentFloor
                dispatchedTo = i
              }
            }
          }
        } else {
          if (elevator.goingDown && elevator.currentFloor >= floor) {
            if (elevator.currentFloor === floor) return i
            if (elevator.minInQueue < floor) {
              if (elevator.currentFloor - floor < inTrailDistance) {
                inTrailDistance = elevator.currentFloor - floor
                dispatchedTo = i
              }
            } else {
              if (inTrailDistance === this.floorNum + 1 && elevator.currentFloor - floor < distance) {
                distance = elevator.currentFloor
                dispatchedTo = i
              }
            }
          }
        }
        if (dispatchedTo < 0) {
          if (elevator.currentFloor === floor ) {
            return i
          }
          console.log("电梯动不动", elevator.idle)
          if (elevator.idle) {
            console.log(Math.abs(floor - elevator.currentFloor))
            console.log(floor, elevator.currentFloor)
            console.log("距离", distance)
            console.log("赋值", distance > Math.abs(floor - elevator.currentFloor))
            if (distance > Math.abs(floor - elevator.currentFloor)) {
              distance = Math.abs(floor - elevator.currentFloor)
              dispatchedTo = i
            }
          }
        }
      }

      if (dispatchedTo < 0) {
        console.log("NO ELEVATOR SELECTED!")
        var min = this.floorNum + 1
        var max = -1
        for (var j = 0; i < this.elevNum; j++) {
          let elevator = this.$refs.elevatorList[j]
          if (direction === UP) {
            if (elevator.minInQueue < min) {
              min = elevator.minInQueue
              dispatchedTo = j
            }
          } else {
            if (elevator.maxInQueue > max) {
              max = elevator.maxInQueue
              dispatchedTo = j
            }
          }
        }
      }

      return dispatchedTo
    }
  }
}

</script>

<style scoped>

</style>