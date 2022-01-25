<template>
  <div class="add-cards">
    <h1>ADD A NEW BANK CARD</h1>
    <p>NEW CARD</p>
    <Form @clickToChangeView="$emit('clickToChangeView')" />
  </div>
</template>

<script>
import Form from '../components/Form.vue';

export default {
  components: { Form },
  data() {
    return {
    };
  },
  methods: {

  },
};
</script>

<style>
.add-cards {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
