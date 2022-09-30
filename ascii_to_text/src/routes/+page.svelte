<script lang="ts">
	import Input from '$lib/components/input.svelte';
</script>

<svelte:head>
	<title>Pixel Art To Ascii Generator</title>
	<meta name="description" content="Pixel Art To Ascii Generator" />
</svelte:head>

<div class="container">
	<div class="canvas">This is Canvas</div>
	<div class="select-form">
		<Input />
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-direction: row;
		width: 100vw;
		height: 100vh;
	}

	.canvas {
		height: 100vh;
		min-width: 300px;
		width: 70%;
		background-color: aqua;
	}

	.select-form {
		display: flex;
		flex-direction: column;
		height: 100vh;
		width: 30%;
		background-color: brown;
		align-items: center;
	}
</style>
