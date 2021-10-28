<template>
  <div class="font-sans">
    <Header></Header>
    <FilterBar
      @display-all="displayAll"
      @display-available="displayAvailable"
      @display-saved="displaySaved"
    ></FilterBar>
    <Title :header="header"></Title>
    <ProductTile
      v-for="(product, index) in filteredProducts"
      :key=index
      :product="product"
    ></ProductTile>
    <FilterBar
      @display-all="displayAll"
      @display-available="displayAvailable"
      @display-saved="displaySaved"
    ></FilterBar>
  </div>

</template>

<script>
import axios from 'axios';
import { onBeforeMount, ref } from '@vue/runtime-core';
import Header from './Header.vue'
import Title from './Title.vue'
import ProductTile from './ProductTile.vue'
import FilterBar from './FilterBar.vue'


export default {
  components: {
    ProductTile,
    Title,
    FilterBar,
    Header
  },
  setup () {
    const header = ref(null)
    const filters = ref(null)
    const products = ref(null)
    const filteredProducts = ref([])

    onBeforeMount(() => {
      axios.get('https://gist.githubusercontent.com/benfranke/c33280a8df5f4f9db2e63ad45cab26a4/raw/f3ad6c00ff520c2667305103d5705bcbb57a7778/products.json')
        .then(data => {
          products.value = data.data.products;
          header.value = data.data.header;
          filters.value = data.data.filters;
        });

    })

    function displayAll () {
      filteredProducts.value = products.value;
    }

    function displayAvailable () {
      filteredProducts.value = [];

      products.value.forEach(element => {
        if (element.available == true) {
          filteredProducts.value.push(element)
        }
      })

    }

    return {
      products,
      header,
      filters,
      filteredProducts,
      displayAll,
      displayAvailable
    }
  }
}

</script>
