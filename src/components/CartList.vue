<!--
Copyright Fauna, Inc.
SPDX-License-Identifier: MIT-0
-->
<template>
  <div class="mt-8">
    <div class="flow-root">
      <ul role="list" class="-my-6 divide-y divide-gray-200">
        <CartItem 
          v-for="product in cart" :key="product.product.id" :product="product"
          @remove-item="removeCartItem(product.product.id)"
          />
      </ul>
    </div>
  </div>
</template>

<script>
import CartItem from './CartItem';

export default {
  name: 'CartList',
  components: {
    CartItem
  },
  computed: {
    cart() {
      const store = this.$store.state.cart;
      let cart = [];
      for (const key in store) {
        cart.push(store[key]);
      }
      return cart;
    },    
  },
  methods: {
    removeCartItem(id) {
      this.$store.commit('removeCartItem', id);
    }
  }
}
</script>