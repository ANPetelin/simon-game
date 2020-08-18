<template>
  <div id="app">
    <h1>Game</h1>
    <div class = "grid">
    <GameField     
    :playerStep="playerStep" 
    :task="task"
    :level="level"
    ref="GameField"
    @moveTransition="moveTransition"
    @onPlayerStep="onPlayerStep"
    @changeMessage="changeMessage"
    />
    <Information
    :message="message"     
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
      playerStep: false,
      level: '',
      task: [],
      playerAnsuer: [],
      message: '',
      segments:[,,,]
    }
  },
  components: {
    GameField,
    Information
  },
  methods: {    
    changeMessage (message) {
      this.message = message;
    },
    onPlayerStep (step) {
      let miss = false;
      let newStepPlayer = step;
      this.playerAnsuer.push(newStepPlayer);
      for (let i=0; i<this.playerAnsuer.length; i++) {
        if (this.playerAnsuer[i] != this.task[i]) {
          miss = true;
        }
      }
      if (miss) {
        this.message = 'Вы проиграли на '+ this.round + ' раунде';
        this.round = 0;
        this.moveTransition();
        this.task = [];
        this.playerAnsuer = [];        
      }
      else if (this.playerAnsuer.length === this.task.length) {
        this.round = this.round + 1;
        this.moveTransition();
        this.playerAnsuer = [];
        this.message = 'Ход компьютера';
        setTimeout(() => this.gameStart(), 1000);
      }
      
    },
    moveTransition () {
      this.playerStep = !this.playerStep;
    },
    changeLevel(level) {
      this.level = level;
    },
    onStart() {
      this.level ? this.gameStart() : this.message = 'Установите уровень сложности';
    },
    gameStart() {
      if (!this.playerStep) {
        let newTask = Math.ceil(Math.random()*this.segments.length);
        this.task.push(newTask);
        this.$refs.GameField.computerStep();
      }      
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
