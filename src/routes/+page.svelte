<script>
	import SkyboxIdea from '$lib/ideas/SkyboxIdea.svelte';
	import CurvedImageIdea from '$lib/ideas/CurvedImageIdea.svelte';
	import SkyboxCompressedIdea from '$lib/ideas/SkyboxCompressedIdea.svelte';

	// ensure idea asset elements don't overlap IDs
	let ideaIndex = 0;
	const ideas = [
		{ name: 'curved 1', comp: CurvedImageIdea },
		{ name: 'skybox 2', comp: SkyboxCompressedIdea },
		{ name: 'skybox 1', comp: SkyboxIdea }
	];

	const setIdea = (/** @type {number} */ desiredIdeaIndex) => {
		ideaIndex = desiredIdeaIndex;
	};

	let mute = true;
	const muteBtnPress = () => {
		mute = !mute;
	};

	document.querySelector('#refresh-button')?.addEventListener('click', muteBtnPress);
</script>

<!-- todo: stereo throws console errors trying to reference AFRAME -->
<!-- todo: "multiple instances of AFRAME being imported" -->
<svelte:head>
	<script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>
	<script src="/aframe-stereo-component.min.js"></script>
</svelte:head>

<div class="controls">
	<label>
		<input
			type="button"
			value={mute ? 'unmute' : 'mute'}
			class={mute ? '' : 'active'}
			on:click={muteBtnPress}
		/>
	</label>
	{#each ideas as idea, i}
		<label>
			<input
				type="button"
				value={idea.name}
				class={ideaIndex == i ? 'active' : ''}
				on:click={() => setIdea(i)}
			/>
		</label>
	{/each}
</div>
<!-- todo: disable wasd -->

<a-scene>
	<svelte:component this={ideas[ideaIndex].comp} />

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
