<template>
  <div>
    <div class="simon">
      <ul>
        <li :class="clickOnRed" tile="1" @click="playerStep ? clickHandler(1) : null"></li>
        <li :class="clickOnBlue" tile="2" @click="playerStep ? clickHandler(2) : null"></li>
        <li :class="clickOnYellow" tile="3" @click="playerStep ? clickHandler(3) : null"></li>
        <li :class="clickOnGreen" tile="4" @click="playerStep ? clickHandler(4) : null"></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["task", "level", "playerStep"],
  data() {
    return {
      clickOnRed: "red",
      clickOnBlue: "blue",
      clickOnYellow: "yellow",
      clickOnGreen: "green",
      pause: null,
    };
  },
  methods: {
    computerStep() {
        if (this.level == "легкий") this.pause = 1500;
        else if (this.level == "средний") this.pause = 1000;
        else if (this.level == "тяжелый") this.pause = 400;

        let i = 0;
        let interval = setInterval(() => {
          this.clickHandler(this.task[i]);
          i++;

          if (i >= this.task.length) {
            clearInterval(interval);
            this.$emit('moveTransition');
            this.$emit('changeMessage', 'Ход игрока')
          }
        }, this.pause);
    },
    clickHandler(title) {
        if(this.playerStep) {
            this.$emit('onPlayerStep', title);
        }
      switch (title) {
        case 1:
          this.clickOnRed = this.clickOnRed + " " + "clickOnLi";
          let audio = new Audio("sound/1.mp3");
          audio.play();
          setTimeout(() => (this.clickOnRed = "red"), this.pause * 0.8);
          break;
        case 2:
          this.clickOnBlue = this.clickOnBlue + " " + "clickOnLi";
          let audio2 = new Audio("sound/2.mp3");
          audio2.play();
          setTimeout(() => (this.clickOnBlue = "blue"), this.pause * 0.8);
          break;
        case 3:
          this.clickOnYellow = this.clickOnYellow + " " + "clickOnLi";
          let audio3 = new Audio("sound/3.mp3");
          audio3.play();
          setTimeout(() => (this.clickOnYellow = "yellow"), this.pause * 0.8);
          break;
        case 4:
          this.clickOnGreen = this.clickOnGreen + " " + "clickOnLi";
          let audio4 = new Audio("sound/4.mp3");
          audio4.play();
          setTimeout(() => (this.clickOnGreen = "green"), this.pause * 0.8);
          break;
        default:
          break;
      }
    },
  },
};
</script>


<style scoped>
ul {
  list-style: none;
}
li {
  display: list-item;
  text-align: -webkit-match-parent;
}
ul,
li {
  padding: 0;
  margin: 0;
}
.red,
.blue,
.yellow,
.green {
  opacity: 0.6;
  height: 290px;
  -webkit-border-radius: 150px 150px 150px 150px;
  border-radius: 150px 150px 150px 150px;
  position: absolute;
  text-indent: 10000px;
}
.red {
  background: #ff5643;
  clip: rect(0px, 300px, 150px, 150px);
  width: 296px;
}
.blue {
  background: dodgerblue;
  clip: rect(0px, 150px, 150px, 0px);
  width: 300px;
}
.yellow {
  background: #feef33;
  clip: rect(150px, 150px, 300px, 0px);
  width: 300px;
}
.green {
  background: #bede15;
  clip: rect(150px, 300px, 300px, 150px);
  width: 296px;
}
.clickOnLi {
  opacity: 1;
}
.simon {
  background: #fff;
  position: relative;
  float: left;
  margin-right: 3em;
  width: 302px;
  height: 295px;
  -webkit-border-radius: 150px 150px 150px 150px;
  border-radius: 150px 150px 150px 150px;
  -moz-box-shadow: 2px 1px 12px #aaa;
  -webkit-box-shadow: 2px 1px 12px #aaa;
  -o-box-shadow: 2px 1px 12px #aaa;
  box-shadow: 2px 1px 12px #aaa;
}
.red:hover,
.blue:hover,
.yellow:hover,
.green:hover {
  border: 2px solid black;
}
</style>