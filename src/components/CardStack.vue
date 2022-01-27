
<template>
  <div>
    <Card
      @sendData="$emit('sendData' , card)"
      :card="card"
      v-for="card in cards"
      :key="card.id"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  components: { Card },
  props: { cards: Array, active: Array },

  data() {
    return {};
  },

  methods: {},
};
</script>

<style scoped>
.card-list {
  display: flex;
  flex-direction: column;
}
</style>
