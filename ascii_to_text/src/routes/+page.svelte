<script lang="ts">
	import Input from '$lib/components/input.svelte';
	import Canvas from '$lib/components/Canvas/index.svelte';
</script>

<svelte:head>
	<title>Pixel Art To Ascii Generator</title>
	<meta name="description" content="Pixel Art To Ascii Generator" />
</svelte:head>

<div class="container">
	<Canvas rows ={10} cols= {10} />
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

	.select-form {
		display: flex;
		flex-direction: column;
		height: 100vh;
		width: 30%;
		background-color: brown;
		align-items: center;
	}
</style>
