<template>
<div>
    <div class = "simon">
        <ul>
            <li :class="clickOnRed" tile="1" @click="clickHandler(1)"></li>
            <li :class="clickOnBlue" tile="2" @click="clickHandler(2)"></li>
            <li :class="clickOnYellow" tile="3" @click="clickHandler(3)"></li>
            <li :class="clickOnGreen" tile="4" @click="clickHandler(4)"></li>
        </ul>              
    </div>
    <button @click="test">проиграть</button>  
    </div>
</template>

<script>

export default {
    props: ['task', 'level'],
    data() {
        return{
            clickOnRed: 'red',
            clickOnBlue: 'blue',
            clickOnYellow: 'yellow',
            clickOnGreen: 'green'
        }
    },
    methods: {
        test () {
            this.task.forEach(element => {
                this.clickHandler(element);
            });
        },
        sleep(milliseconds) {
            const date = Date.now();
            let currentDate = null;
            do {
                currentDate = Date.now();
            } while (currentDate - date < milliseconds);
        },
        clickHandler(title) {
                let pause = null;
                if (this.level == 'легкий') pause = 1500;
                else if (this.level == 'средний') pause = 1000;
                else if (this.level == 'тяжелый') pause = 400;

            switch(title) {
                case 1:
                    this.clickOnRed = this.clickOnRed + ' ' + 'clickOnLi';
                    let audio = new Audio('mp3/1.mp3');
                    audio.play();
                    setTimeout(() => this.clickOnRed = 'red', 500);                    
                    break;
                case 2:
                    this.clickOnBlue = this.clickOnBlue + ' ' + 'clickOnLi';
                    let audio2 = new Audio('mp3/2.mp3');
                    audio2.play();
                    setTimeout(() => this.clickOnBlue = 'blue', 500);
                    break;
                case 3:
                    this.clickOnYellow = this.clickOnYellow + ' ' + 'clickOnLi';
                    let audio3 = new Audio('mp3/3.mp3');
                    audio3.play();
                    setTimeout(() => this.clickOnYellow = 'yellow', 500);
                    break;
                case 4:
                    this.clickOnGreen = this.clickOnGreen + ' ' + 'clickOnLi';
                    let audio4 = new Audio('mp3/4.mp3');
                    audio4.play();
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