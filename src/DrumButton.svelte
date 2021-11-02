<script>
	export let letter = "Q"
	export let source = "./sounds/kick.wav"
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	let pressed = false
	let paused = true
	let audio
	
	function handleKeydown() {
		if (event.key == letter.toLowerCase()) {
			press()
		}
	}
	
	function press() {
		audio.currentTime = 0
		audio.play()
		pressed = true
		setTimeout(()=>{pressed=false}, 150)
		dispatch('soundPlayed', {
			name: source.split("/")[2]
		});
	}
	
</script>

<svelte:window on:keydown={handleKeydown}/>

<div class:pressed on:mousedown={press}>
	<p>{letter}</p>
	<audio bind:paused src={source} bind:this={audio}>
		
	</audio>
</div>

<style>
	div {
		display: flex;
		margin: .5rem;
		border: 2px solid black;
		box-shadow: 4px 4px 0 black;
		cursor:pointer;
	}
	p {
		padding: 0;
		margin: auto;
		font-size: 4rem;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}
	.pressed {
		transform: translate(4px,4px);
		box-shadow: 0 0 0 black;
	}
</style>