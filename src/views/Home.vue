<template>
  <div id="home-view">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
    </header>

    <div class="active-card">
      <Card :card="modelCard" v-if="modelCard" />
    </div>
    <br /><br />

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

.card-list {
  /* nu hamnar knappen alltid under korten
  height: 660px;
  width: 386px; */
  margin-top: 40px;
}

.add-button {
  background-color: white;
  color: black;
  margin-top: 50px;
}
</style>
