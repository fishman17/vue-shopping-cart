<template>
  <ul>
      <li v-for="product in products" :key="product.id">
          {{product.title}} - {{product.price}}
          <br>
          <button :disabled="!product.inventory" @click="addToCart(product)">Add to cart</button>
      </li>
  </ul>
</template>
<script>
import {mapGetters, mapActions} from 'vuex'
// this.$store.getters  mapGetters
// this.$store.dispatch() mapActions
export default {
//   computed: mapGetters({
//     products: 'allProducts'
//   }),
  created () {
    this.$store.dispatch('getAllProducts')
  },
  computed: {
      products(){
          return this.$store.getters.allProducts;
          console.log(this.$store.getters.allProducts);
      }
  },
  methods:mapActions(['addToCart']),
}
</script>
<style>

</style>
