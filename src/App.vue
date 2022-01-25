<template>
  <div id="app">
    <Home v-if="currentView == 'home'" @clickToChangeView="changeView" />
    <AddCards v-else @clickToChangeView="changeView" />
  </div>
</template>

<script>
import Home from './views/Home.vue';
import AddCards from './views/AddCards.vue';

export default {
  name: 'App',
  components: { Home, AddCards },
  data() {
    return {
      currentView: 'home',
    };
  },
  
  methods: {
    changeView() {
      if (this.currentView == "home" ) {
        this.currentView = 'addCards';
      } else {
        this.currentView = 'home';
      }
    }
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&display=swap');

#app {
  display: flex;
  justify-content: center;
  margin: auto;
  text-transform: uppercase;
  border-radius: 6px;
}

h1 {
  font-family: 'Source Sans Pro', sans-serif;
}

input {
  font-family: 'PT Mono', monospace;
}

button {
  font-family: 'PT Mono', monospace;
  font-size: 22px;
  width: 382px;
  height: 72px;
  border-radius: 8px;
}
</style>
