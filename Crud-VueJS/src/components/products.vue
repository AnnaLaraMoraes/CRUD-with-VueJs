<template>
  <div id='products'>
    <div v-bind:key="product.id" v-for="product in products">
      <ProductItem v-bind:product="product" v-on:del-product="$emit('del-product', product.id)" />
    </div>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';
export default {
  name: "Products",
  components: {
    ProductItem
  },
  props: ["products"]
}
</script>

<style scoped>

</style>


