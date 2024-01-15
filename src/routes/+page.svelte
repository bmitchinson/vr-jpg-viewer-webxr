<script>
	let mute = true;

	const muteBtnPress = () => {
		mute = !mute;
	};
</script>

<svelte:head>
	<script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
	<script src="/aframe-stereo-component.min.js"></script>
</svelte:head>

<div class="controls">
	<label>
		<input type="button" value={mute ? 'unmute' : 'mute'} on:click={muteBtnPress} />
	</label>
</div>

<a-scene>
	<a-assets>
		<!-- svelte-ignore a11y-missing-attribute -->
		<img id="left" src="/left.jpg" />
		<!-- svelte-ignore a11y-missing-attribute -->
		<img id="right" src="/right.jpg" />

		<audio id="recording" src="/audio.mp4" preload="auto"></audio>
	</a-assets>

	<a-sky id="sky1" src="#left" stereo="eye:left"></a-sky>
	<a-sky id="sky2" src="#right" stereo="eye:right"></a-sky>

	{#if !mute}
		<a-entity
			id="ambient"
			geometry="primitive: plane"
			material="color: blue"
			position="0 0 0"
			sound="src: #recording; autoplay: true; loop: true"
		></a-entity>
	{/if}
</a-scene>

<style>
	.controls {
		position: absolute;
		bottom: 2em;
		left: 2em;
		z-index: 2;
	}

	input {
		height: 2em;
		width: 5em;
	}
</style>
