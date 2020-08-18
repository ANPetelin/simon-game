<template>
  <div id="app">
    <h1>Game</h1>
    <h4>{{level != '' ? 'Выбран '  + level + ' уровень сложности': 'Выберете уровень сложности'}}</h4>
    <div class = "grid">
    <GameField 
    :task="task"
    :level="level"
    />
    <Information     
    :round="round"
    @changeLevel="changeLevel"
    @onStart="onStart"/>
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
      round: 0,
      level: '',
      task: [1,2,4,3],
      playerAnsuer: [],
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
    changeLevel(level) {
      this.level = level;
    },
    onStart() {
      console.log('kdhvcb');
    }
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
    text-align: center;
}
h4 {
  margin-bottom: 4em;
    text-align: center;
}
</style>
