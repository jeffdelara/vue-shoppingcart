<template>
  <div id="app">
    <header>GameShop</header>
    <search-component :games="games" />

    <div id="store">
      <div id="displays">
        <game-component
          v-for="game in games"
          :addToCart="addToCart"
          :key="game.id"
          :game="game"
        />
      </div>
      <cart-items :cart="cart" :removeFromCart="removeFromCart" />
    </div>
  </div>
</template>

<script>
import GameComponent from "./components/GameComponent.vue";
import CartItems from "./components/CartItems.vue";
import SearchComponent from "./components/SearchComponent.vue";

export default {
  name: "App",

  created() {
    console.log("created");
  },

  mounted() {
    console.log("mounted");
  },

  updated() {
    console.log("updated");
  },

  destroyed() {
    console.log("destroyed");
  },

  data: () => ({
    cart: [],
    games: [
      {
        id: 1,
        title: "Elden Ring",
        description: `THE NEW FANTASY ACTION RPG. Rise, Tarnished, 
          and be guided by grace to brandish the power of the Elden Ring and become an Elden Lord in the Lands Between.`,
        price: 1995,
        releaseDate: "Feb 25, 2022",
        developer: "FromSoftware Inc.",
        thumb: "/images/elden-ring.jpeg",
        visible: true,
      },
      {
        id: 2,
        title: "Lost Ark",
        description: `Ark is a free-to-play game that pairs the best of ARPG combat and MMO depth to create a vast, vibrant world with thrilling fights.`,
        price: 599,
        releaseDate: "Dec 4, 2019",
        developer: "Smilegate",
        thumb: "/images/lost-ark.jpeg",
        visible: true,
      },
      {
        id: 3,
        title: "Fall Guys",
        description: `Fall Guys is a massively multiplayer party game with up to 60 players online in a free-for-all struggle through round after round of escalating chaos until one victor remains!`,
        price: 599,
        releaseDate: "Aug 4, 202020",
        developer: "Mediatonic",
        thumb: "/images/fall-guys.png",
        visible: true,
      },
      {
        id: 4,
        title: "Counter Strike: GO",
        description: `Fall Guys is a massively multiplayer party game with up to 60 players online in a free-for-all struggle through round after round of escalating chaos until one victor remains!`,
        price: 599,
        releaseDate: "Aug 4, 202020",
        developer: "Mediatonic",
        thumb: "/images/counter-strike.jpeg",
        visible: true,
      },
    ],
  }),

  methods: {
    addToCart(game) {
      const foundGame = this.cart.filter((g) => {
        return g.id === game.id;
      });

      if (foundGame.length === 0) {
        game.quantity = 1;
        this.cart.push(game);
      } else {
        const game = foundGame[0];
        game.quantity += 1;

        const uniqueCart = this.cart.filter(
          (v, i, a) => a.findIndex((t) => t.id === v.id) === i
        );
        this.cart = uniqueCart;
      }
    },

    removeFromCart(id) {
      const newCart = this.cart.filter((item) => {
        return item.id != id;
      });

      this.cart = newCart;
    },
  },

  components: { GameComponent, CartItems, SearchComponent },
};
</script>
