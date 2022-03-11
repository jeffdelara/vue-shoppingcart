<template>
  <div class="card" v-if="game.visible">
    <h2>{{ game.title }}</h2>
    <img :src="game.thumb" />
    <div class="price">P{{ game.price }}</div>
    <div class="description">
      {{ game.description }}
    </div>
    <button v-on:click="addToCart(game)">Add to cart</button>
  </div>
</template>

<script>
export default {
  name: "GameComponent",
  props: ["game", "addToCart"],
  data: () => ({}),
  methods: {},
};
</script>

<style
  lang="scss"
  scoped
  src="../styles/components/_game-card-component.scss"
/>
