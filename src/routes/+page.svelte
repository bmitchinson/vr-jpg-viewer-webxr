<script>
	import SkyboxIdea from '$lib/ideas/SkyboxIdea.svelte';
	import CurvedImageIdea from '$lib/ideas/CurvedImageIdea.svelte';

	const defaultIdea = 1;
	let ideaIndex = defaultIdea;
	const setIdea = (/** @type {number} */ desiredIdeaIndex) => {
		ideaIndex = desiredIdeaIndex;
	};

	let mute = true;
	const muteBtnPress = () => {
		mute = !mute;
	};

	document.querySelector('#refresh-button')?.addEventListener('click', muteBtnPress);
</script>

<svelte:head>
	<script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
	<script src="/aframe-stereo-component.min.js"></script>
</svelte:head>
<!-- todo: stereo throws console errors trying to reference AFRAME -->
<!-- todo: "multiple instances of AFRAME being imported" -->

<div class="controls">
	<label>
		<input
			type="button"
			value={mute ? 'unmute' : 'mute'}
			class={mute ? '' : 'active'}
			on:click={muteBtnPress}
		/>
	</label>
	<label>
		<input
			type="button"
			value="skybox 1"
			class={ideaIndex == 0 ? 'active' : ''}
			on:click={() => setIdea(0)}
		/>
	</label>
	<label>
		<input
			type="button"
			value="curved 1"
			class={ideaIndex == 1 ? 'active' : ''}
			on:click={() => setIdea(1)}
		/>
	</label>
</div>
<!-- todo: disable wasd -->

<a-scene>
	<a-assets>
		<audio id="recording-asset" src="/audio.mp4" preload="auto"></audio>
		<img id="blur-sky-asset" src="/skybox_sample_blur.jpg" />
		<img id="left-strip-asset" src="/left_no_boundaries.jpg" />
		<img id="right-strip-asset" src="/right_no_boundaries.jpg" />
		<img id="left-equir-asset" src="/left_equirectangular.jpg" />
		<img id="right-equir-asset" src="/right_equirectangular.jpg" />
	</a-assets>

	<!-- ensure idea asset elements don't overlap IDs -->
	{#if ideaIndex == 0}
		<SkyboxIdea />
	{/if}
	{#if ideaIndex == 1}
		<CurvedImageIdea />
	{/if}

	{#if !mute}
		<a-entity
			id="ambient"
			geometry="primitive: plane"
			material="color: blue"
			position="0 0 0"
			sound="src: #recording-asset; autoplay: true; loop: true"
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

	.active {
		background-color: lightskyblue;
	}
</style>
