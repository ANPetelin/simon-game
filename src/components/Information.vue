<template>  
<div class = "information">
    <h2>Round: {{round}}</h2>
    <button class = "button" @click="onStart">Start</button>    
    <p>{{ message }}</p>
    <div class="game-options" @change="changeLevel">
			<h2>Game Options:</h2>
                <input type="radio" id="one" value="легкий" v-model="picked">
                <label for="one">Легкий</label><br>
                <input type="radio" id="two" value="средний" v-model="picked">
                <label for="one">Средний</label><br>
                <input type="radio" id="three" value="тяжелый" v-model="picked">
                <label for="one">Тяжелый</label><br>
	</div>  
</div>
</template>

<script>
export default {
  props: ['round'],
  data() {
      return {
        picked: '',
        message: '',
      }    
  }, 
  methods: {
      changeLevel() {
          if(this.picked.trim()) {
          let newLevel = this.picked;
          this.$emit('changeLevel', newLevel);
          }          
      },
      onStart() {
          this.$emit('onStart');
      }
  }
}
</script>



<style scoped>
.information {
padding-left: 80px;
}
.button {
    width: 5em;
    box-sizing: border-box;
    font-size: 1.4em;
    -webkit-border-radius: 10px 10px 10px 10px;
    border-radius: 10px 10px 10px 10px;
    background: #6DABE8;
    border: none;
    padding: 0.3em 0.6em;
}
p {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
}
</style>