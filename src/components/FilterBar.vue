<template>
  <div class="flex">
    <button
      type="button"
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 flex-auto text-center"
      @click="displayAll"
    >Alle</button>
    <button
      type="button"
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 flex-auto"
      @click="displayAvailable"
    >Verfügbar</button>
    <button
      type="button"
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 flex-auto"
      @click="displaySaved"
    >Vorgemerkt</button>
  </div>
</template>

<script>
export default {
  setup (props, context) {
    function displayAll () {
      context.emit('display-all')
    }
    function displayAvailable () {
      context.emit('display-available')
    }
    function displaySaved () {
      context.emit('display-saved')
    }

    return {
      displayAll,
      displayAvailable,
      displaySaved
    }
  }
}

</script>