<template>
  <div class="py-1 flex flex-col justify-center sm:py-2">
    <div class="relative py-3 sm:mx-auto mx-auto">

      <div class="relative inline-flex bg-gradient-to-r from-cyan-400 to-light-blue-500 shadow-lg sm:rounded-3xl rounded-xl sm:p-5 p-2">

        <div class="">
          <div class="p-1 sm:p-2">
            <button class="border-solid border-4 rounded-lg border-gray-500" :key="currentFloor +'button-up'">
              <svg class="h-8 sm:h-14 sm:w-14 p-1" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="50" height="50"><path
                  d="M0 1024 1316.571429 1024 658.285714 0 0 1024Z" fill="#cdcdcd"></path></svg>
            </button>
          </div>

          <div class="p-1 sm:p-2">
            <button class="border-solid border-4 rounded-lg border-gray-500" :key="currentFloor +'button-down'">
              <svg class="h-8 sm:h-14 sm:w-14 p-1" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="50" height="50"><path
                  d="M0 0 1316.571429 0 658.285714 1024 0 0Z" fill="#cdcdcd"></path></svg>
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
    currentFloor: Number
  },
  data() {
    return {

    }
  }
}
</script>

<style scoped>

</style>