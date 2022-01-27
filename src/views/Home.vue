<template>
  <div id="home-view">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
    </header>

    <Card :card="modelCard" />

    <div class="card-list">
      <CardStack :cards="cards" @sendData="myMethod" />
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
      modelCard: {

      },
    };
  },

  methods: {
    myMethod(info) {
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

.active-card {
  height: 200px;
  width: 386px;
  background-color: #d0d0d0;
  box-shadow: 0px 0px 5px 5px rgba(0, 0, 0, 0.32);

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
