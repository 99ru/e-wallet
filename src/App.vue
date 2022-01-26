<template>
  <div id="app">
    <Home
      v-if="currentView == 'home'"
      @clickToChangeView="changeView"
      :cards="cards"
    />

    <AddCards
      v-else
      @clickToChangeView="changeView"
      @emit-card="registerCard"
    />
  </div>
</template>

<script>
import Home from "./views/Home.vue";
import AddCards from "./views/AddCards.vue";


export default {
  name: "App",
  components: { Home, AddCards },
  data() {
    return {
      currentView: "home",

      cards: [
        {
          id: 0,
          cardNumber: "1337420069696666",
          name: "Lennart Bladh",
          year: "2024",
          month: "12",
          vendor: {
            name: "Bitcoin Inc",
            backgroundColor: "#FFAE34",
            fontColor: "black",
            logo: require("./assets/bitcoin.svg"),
          },
        },
        {
          id: 1,
          cardNumber: "1234567890123456",
          name: "Lars Filipsson",
          year: "2022",
          month: "12",
          vendor: {
            name: "Ninja Bank",
            backgroundColor: "#222222",
            fontColor: "black",
            logo: require("./assets/ninja.svg"),
          },
        },
      ],
    };
  },

  methods: {
    changeView() {
      if (this.currentView == "home") {
        this.currentView = "addCards";
      } else {
        this.currentView = "home";
      }
    },

    registerCard(value) {
      this.cards.push({
        id: this.cards.length,
        cardNumber: value.cardNumber,
        name: value.name,
        year: value.year,
        month: value.month,
        vendor: value.vendor,
      });
      console.log(this.cards);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&display=swap");
html {
  background: grey;
}
#app {
  display: flex;
  justify-content: center;
  margin: auto;
  text-transform: uppercase;
  border-radius: 6px;
  width: 500px;
  height: 1000px;
  border-radius: 3rem;
  /*  border: 3px solid black; */

  /* background: white; */
}

h1 {
  font-family: "Source Sans Pro", sans-serif;
}

input {
  font-family: "PT Mono", monospace;
}

button {
  font-family: "PT Mono", monospace;
  font-size: 22px;
  width: 382px;
  height: 72px;
  border-radius: 8px;
}
</style>
