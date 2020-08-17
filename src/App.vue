<template>
  <div id="app">
    <h1>Game</h1>
    <div class = "grid">
    <GameField />
    <Information />
    </div>
  </div>
</template>

<script>
import GameField from './components/GameField';
import Information from './components/Information';

export default {
  name: 'App',
  data() {
    return {      
      segments:[
        {id: 1, color: "red"},
        {id: 2, color: "blue"},
        {id: 3, color: "yellow"},
        {id: 4, color: "green"}
      ]
    }
  },
  components: {
    GameField,
    Information
  },
  methods: {
  }
}
</script>

<style>
#app {
    width: 540px;
    margin: 0 auto;    
}
.grid {
    display: grid;
    grid-template-columns: 45% 45%;
    grid-gap: 1em;
}
h1 {
    margin: 1em 0 2em;
    text-align: center;
}
</style>
