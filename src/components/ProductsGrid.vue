<template>
  <div class="grid-wrap">
      <products-grid-item
      v-for="product in products"
      :key="product.id"
      :product="product" />
  </div>
</template>

<script>
import ProductsGridItem from './ProductsGridItem.vue'
export default {
    name: 'ProductsGrid',
    props: ['products'],
    components: { ProductsGridItem }
}
</script>

<style scoped>
  .grid-wrap {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-top: 16px;
  }

  @media screen and (max-width: 500px) {
    .grid-wrap {
      flex-direction: column;
      align-items: center;
    }
  }
</style>