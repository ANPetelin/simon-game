<template>
    <div class = "simon">
        <ul>
            <li :class="clickOnRed" tile="1" @click="clickHandler(1)"></li>
            <li :class="clickOnBlue" tile="2" @click="clickHandler(2)"></li>
            <li :class="clickOnYellow" tile="3" @click="clickHandler(3)"></li>
            <li :class="clickOnGreen" tile="4" @click="clickHandler(4)"></li>
        </ul>
    </div>
</template>

<script>

export default {
    data() {
        return{
            clickOnRed: 'red',
            clickOnBlue: 'blue',
            clickOnYellow: 'yellow',
            clickOnGreen: 'green'
        }
    },
    methods: {
        clickHandler(title) {
            switch(title) {
                case 1:
                    this.clickOnRed = this.clickOnRed + ' ' + 'clickOnLi';
                    // let audioRed = new Audio('../mp3/1');
                    // audioRed.play();
                    setTimeout(() => this.clickOnRed = 'red', 500);                    
                    break;
                case 2:
                    this.clickOnBlue = this.clickOnBlue + ' ' + 'clickOnLi';
                    setTimeout(() => this.clickOnBlue = 'blue', 500);
                    break;
                case 3:
                    this.clickOnYellow = this.clickOnYellow + ' ' + 'clickOnLi';
                    setTimeout(() => this.clickOnYellow = 'yellow', 500);
                    break;
                case 4:
                    this.clickOnGreen = this.clickOnGreen + ' ' + 'clickOnLi';
                    setTimeout(() => this.clickOnGreen = 'green', 500);
                    break;
                default:
                    break;
            }
        }
    }
}
</script>


<style scoped>
ul {
    list-style: none;
}
li {
    display: list-item;
    text-align: -webkit-match-parent;
}
ul, li {
    padding: 0;
    margin: 0;
}
.red, .blue, .yellow, .green {
    opacity: 0.6;
    height: 290px;
    -webkit-border-radius: 150px 150px 150px 150px;
    border-radius: 150px 150px 150px 150px;
    position: absolute;
    text-indent: 10000px;
}
.red {
    background: #FF5643;
    clip: rect(0px, 300px, 150px, 150px);
    width: 296px;
}
.blue {
    background: dodgerblue;
    clip: rect(0px, 150px, 150px, 0px);
    width: 300px;
}
.yellow {
    background: #FEEF33;
    clip: rect(150px, 150px, 300px, 0px);
    width: 300px;
}
.green {
    background: #BEDE15;
    clip: rect(150px,300px, 300px, 150px);
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
.red:hover, .blue:hover, .yellow:hover, .green:hover {
    border: 2px solid black;
}
</style>