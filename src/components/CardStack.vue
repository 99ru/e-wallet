
<template>
  <div>
    <div class="grid-container">
      <Card
      @sendData="$emit('sendData' , card)"
      :card="card"
      v-for="card in cards"
      :key="card.id"
    />
    </div>
    
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  components: { Card },
  props: { cards: Array, active: Array },

  data() {
    return {
      
    };
  },

  methods: {},
};
</script>

<style scoped>
/* .card-list {
  display: flex;
  flex-direction: column;
} */

.grid-container{
  display:grid;
  grid-auto-rows: 2rem;
  height: 400px;
}

</style>
