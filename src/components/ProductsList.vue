<template>
  <div v-if="cartItems.length > 0">
    <products-list-item 
    v-for="product in cartItems"
    @remove-from-cart="$emit('remove-from-cart', $event)"
    :key="product.id"
    :product="product"
    />
  </div>
  <p v-else>Wow! Such Empty, start shopping to see items in your cart! </p>
</template>

<script>
import ProductsListItem from './ProductsListItem.vue'
export default {
    name: 'ProductsList',
    props: ['cartItems'],
    components: { ProductsListItem }

}
</script>
