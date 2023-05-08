<template>
  <div id="home-view">
    <header>
      <h1>E-WALLET</h1>
      <h4>ACTIVE CARD</h4>
    </header>

    <div class="active-card">
      <Card :card="modelCard" v-if="modelCard" />
      <p v-if="!cards.length">You have no cards in your wallet yet.</p>
    </div>
   
   

    <div class="list">
      <CardStack :cards="cards" @sendData="activeClick" />
    </div>

    
    
    <button @click="$emit('toggleView')" class="add-button">
      ADD A NEW CARD
    </button>
  </div>
</template>

<script>
import CardStack from "../components/CardStack.vue";
import Card from "../components/Card.vue";

export default {
  components: { CardStack, Card },
  props: {
    cards: { type: Array, Object },
  },
  data() {
    return {
      modelCard: this.cards[0],
    };
  },

  methods: {
    activeClick(info) {
      this.modelCard = info;
      console.log(info);
    },
  },
  
};
</script>
<style>
header {
  text-align: center;
}
#home {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.active-card{
  margin-bottom: 30px;
}
</style>
