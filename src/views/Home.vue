<template>
  <div id="home-view">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
      <div class="active-card"></div>
    </header>
   
    
    <div class="card-list">
     <!--  <Card /> -->
      <CardStack :cards="cards"/>
    </div>

    <button @click="$emit('toggleView')" class="add-button">
      ADD A NEW CARD
    </button>
    
  </div>
</template>

<script>
import CardStack from "../components/CardStack.vue";
/* import Card from "../components/Card.vue"; */ 
export default {

  components: { CardStack,  },
  props: {
    cards: {type: Array,Object},
  },

  data() {
    return {
    };
  },

  methods: {
    myMethod(info) {
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
  margin-top: 40px
}

.add-button {
  background-color: white;
  color: black;
  margin-top: 50px;

}

.active-card {
  height: 200px;
  width: 386px;
  background-color: #D0D0D0;
  box-shadow: 0px 0px 5px 5px rgba(0, 0, 0, 0.32);
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
