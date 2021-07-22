<template>
  <div id="page-wrap">
    <products-grid :products="products" />
  </div>
</template>

<script>
import { products } from "../fake-data";
import ProductsGrid from "../components/ProductsGrid.vue"

export default {
    name: 'ProductsPage',
    components: { ProductsGrid },
    data() {
      return {
        products
      }
    }
}
</script>
