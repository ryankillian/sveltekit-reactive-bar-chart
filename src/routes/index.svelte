<script>
	import Chart from './chart.svelte';
	let data = [65, 59, 80, 81, 56, 55, 40];
</script>

<input type="text" bind:value={data[0]} />
<input type="text" bind:value={data[1]} />
<input type="text" bind:value={data[2]} />
<input type="text" bind:value={data[3]} />
<input type="text" bind:value={data[4]} />
<input type="text" bind:value={data[5]} />
<input type="text" bind:value={data[6]} />

<Chart newData={data} />

<style>
	input {
		display: block;
	}
</style>
