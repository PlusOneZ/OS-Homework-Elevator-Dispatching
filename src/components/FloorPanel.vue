<template>
  <div class="py-1 flex flex-col justify-center sm:py-2">
    <div class="relative py-3 sm:mx-auto mx-auto bg-cyan-200">

      <div class="relative inline-flex shadow-lg sm:rounded-3xl rounded-xl bg-gradient-to-bl from-blue-300 to-blue-500  sm:p-5 p-2">

        <div>
          <div class="p-1 sm:p-2" v-if="canUp">
            <button
                class="border-solid border-4 rounded-lg border-gray-500 bg-white" :key="currentFloor +'button-up'"
                @click="clickButton('up')"
            >
              <svg class="h-8 sm:h-14 sm:w-14 p-1" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="50" height="50"><path
                  d="M0 1024 1316.571429 1024 658.285714 0 0 1024Z"
                  :fill="upLighten ? '#fcd217' : '#cdcdcd'"
              ></path></svg>
            </button>
          </div>

          <div class="p-1 sm:p-2" v-if="canDown">
            <button
                class="border-solid border-4 rounded-lg border-gray-500 bg-white" :key="currentFloor +'button-down'"
                @click="clickButton('down')"
            >
              <svg class="h-8 sm:h-14 sm:w-14 p-1" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="50" height="50"><path
                  d="M0 0 1316.571429 0 658.285714 1024 0 0Z"
                  :fill="downLighten ? '#fcd217' : '#cdcdcd'"
              ></path></svg>
            </button>
          </div>
        </div>

        <div class="text-5xl sm:py-14 sm:px-5 font-mono font-extrabold px-4 py-6">
          {{ currentFloor }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FloorPanel",
  props: {
    currentFloor: Number,
    canUp: Boolean,
    canDown: Boolean
  },
  data() {
    return {
      upLighten: false,
      downLighten: false,
    }
  },
  methods: {
    clickButton: function (type) {
      if (type === "up") {
        this.upLighten = true
        this.$emit("upRequest", this.currentFloor)
      } else {
        this.downLighten = true
        this.$emit("downRequest", this.currentFloor)
      }
    },

    upRequestHandled: function () {
      this.upLighten = false
    },

    downRequestHandled: function () {
      this.downLighten = false
    }
  }
}
</script>

<style scoped>

</style>