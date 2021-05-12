<template>
  <div class="flex py-6">
    <div class="relative sm:max-w-xl sm:mx-auto text-center">
      <div class="relative px-4 bg-white shadow-lg sm:rounded-3xl sm:p-10">
        <div class="inline-flex bg-green-800 pr-6 p-3 rounded-3xl">
          <div class="sm:-mx-14 inline-block">
          <span>
          <svg class="h-7 sm:h-8" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="200" height="200"><path
              d="M0 1024 1316.571429 1024 658.285714 0 0 1024Z" fill="#cdcdcd"></path></svg>
          </span>
            <p class="h-2"></p>
            <span>
          <svg class="h-7 sm:h-8" viewBox="0 0 1317 1024" xmlns="http://www.w3.org/2000/svg" width="200" height="200"><path
              d="M0 0 1316.571429 0 658.285714 1024 0 0Z" fill="#cdcdcd"></path></svg>
          </span>
          </div>
          <div class="inline-block">
            <p class="h-8 font-mono text-7xl text-white"> {{ currentFloor }} </p>
          </div>
        </div>

        <div class="grid gap-4 grid-cols-4 pt-8">
          <div
              v-for="i in floorNum"
              :key="elevName + ' ' + (floorNum-i) + ' floor'"
          >
            <button
                class="rounded border-2 border-solid bg-cyan-200 border-cyan-300 h-7 w-8"
            >
              {{ floorNum - i }}
            </button>
          </div>
        </div>

        <div class="grid gap-4 grid-cols-4 pt-5">
          <div></div>
          <div></div>
          <div>
            <button>
            <svg class="h-7 rounded border-2 border-solid border-red-300 bg-red-400 w-8 " viewBox="0 0 1024 1024"
                 xmlns="http://www.w3.org/2000/svg" width="200" height="200">
              <path
                  d="M790.87 666.95V456.08c0-144.36-102.62-264.33-236.2-285.65v-85.1h-85.33v85.12c-133.5 21.39-236.03 141.32-236.03 285.61 0 11.4-0.04 33.6-0.04 33.68v176.08c0 30.49-6.92 102.78-70.98 115.6L128 788.3v79.92h147.85l152.19 0.31c7.17 39.88 42.02 70.14 83.96 70.14 41.82 0 76.59-30.09 83.9-69.8l152.17 0.31H896v-79.92l-34.29-6.86c-63.94-12.81-70.85-84.95-70.84-115.45zM290.93 782.91c17.91-32.15 27.68-71.99 27.68-117.22V489.82s0.04-22.3 0.04-33.75c0-112.31 86.78-203.68 193.45-203.68s193.45 91.37 193.45 203.68V668.41c0.2 44.46 9.9 83.67 27.54 115.4l-442.16-0.9z"
                  fill="#f4ea2a"></path>
              <path
                  d="M289.31 242.65l-54.35-65.78C134.44 259.91 76.8 382.25 76.8 512.5h85.33c0-104.72 46.36-203.08 127.18-269.85zM861.87 512.5h85.33c0-130.35-57.72-252.75-158.35-335.8l-54.32 65.81C815.45 309.3 861.87 407.7 861.87 512.5z"
                  fill="#f4ea2a"></path>
            </svg>
            </button>
          </div>
          <div>
            <button>
            <svg class="h-7 rounded border-2 border-solid border-cyan-400 bg-pink-300 w-8 " viewBox="0 0 1025 1024"
                 xmlns="http://www.w3.org/2000/svg" width="200" height="200">
              <path
                  d="M507.918859 650.527512c-49.503789-40.346806-106.623387-94.611243-156.090335-155.822216-34.713235-42.89496-65.404683-87.94306-33.707276-119.633303L95.656089 153.242337C63.221866 193.655661-8.620745 386.103763 299.338585 701.174388c324.458887 332.036833 533.74323 261.005742 569.766359 223.573453L652.205814 708.149578C621.886867 738.400983 582.842793 711.503113 507.918859 650.527512zM947.385483 798.906865l0-0.201601c0 0-169.23738-168.702166-169.343809-168.769707-13.381394-13.347623-34.814547-13.078481-48.127376 0.067541l-61.340939 61.375733 217.469138 217.203066c0 0 61.409504-61.176179 61.342986-61.245767l0.165784-0.132013C961.605005 833.148333 960.162074 811.75202 947.385483 798.906865zM396.298428 297.126091l0-0.168854c14.051691-14.083415 12.74589-35.45005 0-48.196964l0-0.234348c0 0-174.132089-173.597897-174.200654-173.597897-13.452005-13.484753-34.884135-13.148069-48.163193 0l-61.342986 61.441228 222.299375 221.961668C334.888924 358.335017 396.298428 297.225356 396.298428 297.126091z"
                  fill="#1296db"></path>
            </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ElevatorPanel",
  props: {
    currentFloor: Number,
    floorNum: Number,
    elevName: String
  }
}
</script>

<style scoped>

</style>