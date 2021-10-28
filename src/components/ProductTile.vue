<template>
  <div
    class="flex m-4 border-4"
    :class=toggleClass
  >
    <div class="flex-none m-4">
      <img :src=product.imageURL>
    </div>
    <div class="flex-col flex-grow m-4">
      <h1 class="font-bold">{{product.name}}</h1>
      <p class="text-gray-600">{{product.description}}</p>
      <div>
        <p>Preis: {{product.price.value}} {{product.price.currency}}</p>
        <img :src="ratingURL">
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  setup (props) {

    const toggleClass = computed(() => {
      if (props.product.available == true) {
        return 'flex-row'
      }
      else {
        return 'flex-row-reverse'
      }
    })

    const ratingURL = computed(() => {
      let rating = Math.round(props.product.rating * 2) / 2 * 10
      let url = `/assets/stars/${rating}.jpg`
      return url
    })

    return {
      ratingURL,
      toggleClass
    }
  }
}

</script>
