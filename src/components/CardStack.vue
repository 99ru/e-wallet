<template>
  <div class="card-list">
    <Card v-if="!savedCardsArray" :card="card" />
    <Card :card="card" v-for="card in savedCardsArray" :key="card" />
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
