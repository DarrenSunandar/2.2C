<template>
  <div id="app">
    <header>
      <h1>E-commerce Store</h1>
      <button @click="toggleCart">Cart ({{ cart.length }})</button>
    </header>

    <main>
      <product-list :products="products" @add-to-cart="addToCart"></product-list>
    </main>

      <cart v-if="showCart" :cartItems="cart" @remove-item="removeItemFromCart" />
</div>
</template>

<script>
import ProductList from "@/components/ProductList.vue";
import Cart from "@/components/ShoppingCart.vue"; // Assuming that Cart is the correct component name

export default {
  components: {
    ProductList,
    Cart,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          name: 'Green Tea',
          price: 5,
          image: require('@/assets/green-tea.png'),
        },
        {
          id: 2,
          name: 'Milk',
          price: 4,
          image: require('@/assets/milk-picture.png'),
        },
        {
          id: 3,
          name: 'Black Tshirt',
          price: 20,
          image: require('@/assets/black-tshirt.png'),
        },
      ],
      cart: [],
      showCart: false,
    };
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(item) {
      const index = this.cart.findIndex(cartItem => cartItem.id === item.id);
      if (index !== -1) {
        this.cart.splice(index, 1);
      }
    },
    toggleCart() {
      this.showCart = !this.showCart;
    },
  },
};
</script>

<style>
@import "@/styles.css";
</style>
