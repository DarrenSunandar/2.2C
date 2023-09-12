<template>
    <div>
      <h2>Your Cart</h2>
      <ul>
        <li v-for="item in cartItems" :key="item.id">
          {{ item.name }} - {{ item.price }} AUD
          <button @click="removeItem(item)">Delete</button>
        </li>
      </ul>
      <p>Total Price: {{ totalPrice }} AUD</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ShoppingCart',
    props: {
      cartItems: Array,
    },
    methods: {
      removeItem(item) {
        this.$emit('remove-item', item);
      },
    },
    computed: {
        totalPrice() {
            return this.cartItems.reduce((total, item) => total + item.price, 0);
        },
    },
  };
  </script>
  