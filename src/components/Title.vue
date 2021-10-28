<template>
  <div class="m-4">
    <h1 class="text-lg font-bold">{{header.headerTitle}}</h1>
    <h1 class="text-gray-600">{{header.headerDescription}}</h1>
  </div>
</template>

<script>

export default {
  props: {
    header: {
      type: Object,
      required: true
    }
  }
}

</script>