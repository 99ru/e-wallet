<template>
  <div id="app">
    <Home
      v-if="currentView == 'home'"
      @toggleView="changeView"
      :cards="cards"
    />
    <AddCards v-else @toggleView="changeView" @emit-card="registerCard" />
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
          name: "John Doe",
          year: "2024",
          month: "12",
          vendor: {
            name: "Evil Corp",
          backgroundColor: "#F33355",
          fontColor: "white",
          logo: require("./assets/evil.svg"),
          },
        },
        {
          id: 1,
          cardNumber: "1337420069696666",
          name: "Lars åke",
          year: "2023",
          month: "12",
          vendor: {
           name: "Ninja Bank",
          backgroundColor: "#222222",
          fontColor: "white",
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
  background: rgba(255, 251, 251, 0.877);
}
#app {
  display: flex;
  justify-content: center;
  text-transform: uppercase;
  border-radius: 6px;
  border-radius: 3rem;;
}
@media only screen and (max-width: 600px) {
  #app {
    transform: scale(0.7); 
		margin-top: -6rem;
  }

}

h1 {
  font-family: "Source Sans Pro", sans-serif;
}
p {
  font-family: "PT Mono";
}
h4 {
  font-family: "PT Mono";
  color: rgb(102, 96, 96);
}

input {
  font-family: "PT Mono";
}

button {
  font-family: "PT Mono";
  font-size: 22px;
  width: 382px;
  height: 72px;
  border-radius: 8px;
}
</style>
