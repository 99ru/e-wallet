<template>
  <div id="home-view">
    <h1>E-WALLET</h1>
    <h4>ACTIVE CARD</h4>
    <div class="card-list">

       <!-- saved cards  -->
      <CardStack/>
    </div>
    <button @click="$emit('clickToChangeView')" class="add-button">ADD A NEW CARD</button>
  </div>
</template>

<script>
import CardStack from "../components/CardStack.vue";
export default {
  name: 'Home',
  components: { CardStack },
  data() {
    return {
    };
  },
};
</script>

<style>
#home {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-list {
  height: 660px;
  width: 386px;
}

.add-button{
  background-color: white;
  color: black;
}
</style>
