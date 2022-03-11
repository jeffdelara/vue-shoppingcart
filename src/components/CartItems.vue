<template>
  <div class="shopping-cart">
    <h2>Shopping cart</h2>
    <div v-if="cart.length === 0">
      <div class="empty-cart">Oh noes! Empty cart!</div>
    </div>
    <div v-else>
      <div v-for="item in cart" :key="item.id">
        <div class="cart-item">
          <span class="price">P{{ item.price }}</span>
          <img :src="item.thumb" class="small" />
          <b>{{ item.title }}</b> x {{ item.quantity }}
          <br />
          <button class="remove" v-on:click="removeFromCart(item.id)">
            Remove
          </button>
        </div>
      </div>

      <div class="total">TOTAL : P{{ tweenedTotal.toFixed(2) }}</div>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "CartItems",
  props: ["cart", "removeFromCart"],

  updated() {
    this.cartTotal = this.cart.reduce((acc, current) => {
      return acc + current.price * current.quantity;
    }, 0);
  },

  data: () => ({
    cartTotal: 0,
    tweenedTotal: 0,
  }),

  watch: {
    cartTotal(n) {
      gsap.to(this, { duration: 0.5, tweenedTotal: Number(n) || 0 });
    },
  },

  methods: {},
};
</script>

<style lang="scss" scoped src="../styles/components/_cart-items.scss" />
