<script>
	import DrumButton from './DrumButton.svelte'
	let name = 'world';
	let lastSample = '';

	function handleNewSound(event) {
		lastSample = event.detail.name
	}
</script>

<h1>Drum Machine</h1>
<div id="drum-machine">
	<div class="buttonContainer">
		<DrumButton letter="Q" source="./sounds/hat4.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="W" source="./sounds/snare2.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="E" source="./sounds/hat3.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="A" source="./sounds/kick2.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="S" source="./sounds/perc.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="D" source="./sounds/hat2.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="Z" source="./sounds/kick1.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="X" source="./sounds/snare1.wav" on:soundPlayed={handleNewSound}></DrumButton>
		<DrumButton letter="C" source="./sounds/hat1.wav" on:soundPlayed={handleNewSound}></DrumButton>
	</div>
	<p style="text-align:center">{lastSample}</p>
</div>

<style>
	h1 {
		text-align: center;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}
	.buttonContainer {
		display:grid;
		grid-template-columns: 1fr 1fr 1fr;
		grid-template-rows: 1fr 1fr 1fr;
		aspect-ratio: 1 / 1;
		max-width: 30rem;
		margin: auto
	}
</style>