<template>
  <div id="page-wrap" v-if="product">
    <div id="img-wrap">
      <img :src="product.imageUrl" alt="">
    </div>
    <div id="product-details">
      <h1>{{ product.name }}</h1>
      <h3 id="price">£{{ product.price }}</h3>
      <p>Average Rating: {{ product.averageRating}}</p>
      <button 
        id="add-to-cart" 
        @click="addToCart"
        v-if="!showSuccessMessage"
        >Add to Cart</button>
      <button 
        id="add-to-cart"
        class="green-button" 
        v-else
        >Item successfully added to cart</button>
      <h4>Description</h4>
      <p>{{ product.description }}</p>
    </div>
  </div>
  <not-found-page v-else/>
</template>

<script>
import axios from 'axios';
import NotFoundPage from './NotFoundPage.vue';

export default {
  components: { NotFoundPage },
    name: 'ProductDetailPage',
    data() {
      return { 
        product: {},
        showSuccessMessage: false };
    },
    async created() {
      const result = await axios.get(`/api/products/${this.$route.params.id}`);
      const product = result.data;
      this.product = product;
    },
    methods: {
      async addToCart() {
        await axios.post('/api/users/12345/cart', {
          productId: this.$route.params.id
        });
        this.showSuccessMessage = true;
        setTimeout(() => {
          this.$router.push('/products');
        }, 1500);
        
      }
    }
}
</script>

<style scoped>
  #page-wrap {
    margin-top: 16px;
    padding: 16px;
    max-width: 600px;
  }

  #img-wrap {
    text-align: center;
  }

  img {
    width: 400px;
  }

  #product-details {
    padding: 16px;
    position: relative;
  }

  #add-to-cart {
    width: 100%;
  }

  #price {
    position: absolute;
    top: 24px;
    right: 16px;
  }

  .green-button {
    background: green;
  }
</style>