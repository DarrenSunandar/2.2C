<template>
    <div>
      <h2>Product List</h2>
      <div class="product-card" v-for="product in products" :key="product.id">
        <img :src="product.image" :alt="product.name" />
        <h3>{{ product.name }}</h3>
        <p>{{ product.price }} AUD</p>
        <button @click="addToCart(product)">Add to Cart</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      products: Array,
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      },
    },
  };
  </script>
  