<script lang="ts">

	import { onMount } from 'svelte';
	import jQuery from 'jquery';

	onMount(() => {
		window.jQuery = jQuery;
	});

var makeItRain = function() {
  //clear out everything
  jQuery('.rain').empty();

  var increment = 0;
  var drops = "";
  var backDrops = "";

  while (increment < 100) {
    //couple random numbers to use for various randomizations
    //random number between 98 and 1
    var randoHundo = (Math.floor(Math.random() * (98 - 1 + 1) + 1));
    //random number between 5 and 2
    var randoFiver = (Math.floor(Math.random() * (5 - 2 + 1) + 2));
    //increment
    increment += randoFiver;
    //add in a new raindrop with various randomizations to certain CSS properties
    drops += '<div class="drop" style="left: ' + increment + '%; bottom: ' + (randoFiver + randoFiver - 1 + 100) + '%; animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"><div class="stem" style="animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"></div><div class="splat" style="animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"></div></div>';
    backDrops += '<div class="drop" style="right: ' + increment + '%; bottom: ' + (randoFiver + randoFiver - 1 + 100) + '%; animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"><div class="stem" style="animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"></div><div class="splat" style="animation-delay: 0.' + randoHundo + 's; animation-duration: 0.5' + randoHundo + 's;"></div></div>';
  }

  jQuery('.rain.front-row').append(drops);
  jQuery('.rain.back-row').append(backDrops);
}


	function handleBuy(){
		makeItRain();
		console.log("meow?")
	}


</script>

<main>
	<h1>
		Welcome to onlycum.io
	</h1>

	<img id="anti-pic" src="./anti.png" alt="anti"/>
	
	<button id="btn-anim" on:click={handleBuy}><span>Cum 🥛</span></button>
	<div class="rain back-row" style="width:80%; height:40%; margin: auto;"></div>	
	<div class="rain front-row" style="width:80%; height:40%; margin: auto;"></div>
</main>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff004c;
		/* text-transform: uppercase; */
		font-size: 4em;
		font-weight: 500;
	}

	#anti-pic {
		border: 8px dashed rgb(236, 23, 94);
		border-radius: 4px;
		padding: 5px;
	}

	#btn-anim {
		text-align: center;
  		text-decoration: none;
  		display: block;
		margin: 100px auto auto auto;
		padding: 10px 50px;
		background-color: rgb(235, 37, 96);
		color: white;
		font-family: 'Roboto';
		font-size: 1.5em;
		border: none;
		border-radius: 5px;
		transition: all 0.5s;
	  	cursor: pointer;
	}

	#btn-anim:hover {
		padding: 11px 52px;
		background-color: rgb(255, 255, 255);
	}

	#btn-anim span {
		cursor: pointer;
		display: inline-block;
		position: relative;
		transition: 0.5s;
	}

	#btn-anim span:after {
		content: '\00bb';
		position: absolute;
		opacity: 0;
		top: 0;
		right: -20px;
		transition: 0.5s;
	}

	#btn-anim:hover span {
		padding-right: 25px;
	}

	#btn-anim:hover span:after {
		opacity: 1;
		right: 0;
	}

	#btn-anim:active {
		background-color: rgb(150, 44, 58);
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>