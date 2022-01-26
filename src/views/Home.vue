<template>
  <div id="home-view">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>

      <div class="active-card">
        imposter syndrome
      </div>
    </header>
    

    <div class="card-list">
      <CardStack :cards="cards" @sendData="myMethod()"/>
    </div>

    <button @click="$emit('clickToChangeView')" class="add-button">
      ADD A NEW CARD
    </button>
    
  </div>
</template>

<script>
import CardStack from "../components/CardStack.vue";
export default {

  components: { CardStack,  },
  props: {
    cards: {type: Array,},
  },


  data() {
    return {
      activeCardData: {
        cardNumber: "",
        name: "",
        year: "",
        month: "",
        vendor: {},
      },
    };
  },


  methods: {
    myMethod(info) {
      console.log(info);
    },
    activeCard(card){
      this.activeCardData = card;
      this.$emit('click', this.activeCardData);
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

/* .card-list {
  nu hamnar knappen alltid under korten
  height: 660px;
  width: 386px;
} */

.add-button {
  background-color: white;
  color: black;

}

.active-card {
  height: 200px;
  width: 386px;
  background-color: #e2dbdb;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
