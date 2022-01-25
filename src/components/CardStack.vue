<template>
  <div class="card-list">
    <Card :card="card" v-for="card in savedCardsArray" :key="card.id" />
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  components: { Card },
  
  data() {
    return {
      savedCardsArray: [],
      card: {
        cardNumber: "",
        name: "",
        year: "",
        month: "",
        vendor: {},
      },
    };
  },
  
  methods: {

  },

};
</script>

<style scoped>
.card-list {
  display: flex;
  flex-direction: column;
}
</style>
