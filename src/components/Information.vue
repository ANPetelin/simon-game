<template>  
<div class = "information">
    <h2>Round: {{roundNumber}}</h2>
    <button class = "button" >Start</button>
    <div class="game-options">
			<h2>Game Options:</h2>
			<input type="radio" name="mode" value="normal" checked="">Normal<br>
			<input type="radio" name="mode" value="sound-only">Sound Only<br>
			<input type="radio" name="mode" value="light-only">Light Only<br>
			<input type="radio" name="mode" value="free-board">Free board
	</div>
</div>
</template>



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
</style>