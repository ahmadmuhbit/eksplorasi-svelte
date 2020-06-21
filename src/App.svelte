<script>
	import EmojiDisplay from './EmojiDisplay.svelte';
	import EmojiDescription from './EmojiDescription.svelte';

	let isLoaded = false;
	let currentEmoji = '😃';
	const emojis = ['🤣', '🐵', '🙇‍♂️', '🚀'];

	function randomizeEmoji() {
		return emojis[Math.floor(Math.random() * emojis.length)];
	}

	function handleRandomButton() {
		currentEmoji = randomizeEmoji();
	}

	setTimeout(function() {
		isLoaded = true;
	}, 2500);
</script>

<style>	
	div {
		margin: 2em;
	}
</style>

<svelte:head>
	<link href="/terminal.min.css" rel="stylesheet" />
</svelte:head>
<div class="container">
	<h1>Randomize Emoji</h1>
	<ul>
		{#each emojis as emoji}
		<li>{emoji}</li>
		{/each}
	</ul>
	{#if isLoaded === true}
	<EmojiDisplay {currentEmoji} />
	<EmojiDescription />
	<button class="btn btn-primary" on:click={handleRandomButton}>
	🔁 Randomize
	</button>
	{:else}
	<h2>Loading...</h2>
	{/if}
</div>