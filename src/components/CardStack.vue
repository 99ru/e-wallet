<template>
  <div class="card-list">
    <Card :card="card" v-for="card in cards" :key="card.id" />
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  components: { Card },
  props: {
    cards: {
      type: Array,
    },
  },
  
  data() {
    return {
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
