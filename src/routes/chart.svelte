<script>
	import Chart from 'chart.js/auto';

	import { afterUpdate, onMount } from 'svelte';
	import { browser } from '$app/env';

	import { colors, borderColors } from '../utils/colors';

	export let newData = [];

	let myChart;
	let ctx;

	onMount(() => {
		browser && getChart();
	});
	afterUpdate(() => {
		browser && updateChart();
	});

	const labels = ['Alpha', 'Bravo', 'Chalie', 'Delta', 'Romeo', 'Orange'];

	const data = {
		labels: labels,
		datasets: [
			{
				label: 'Stacks',
				data: newData,
				backgroundColor: colors,
				borderColor: borderColors,
				borderWidth: 1
			}
		]
	};

	const config = {
		type: 'bar',
		data: data,
		options: {
			scales: {
				y: {
					beginAtZero: true
				}
			}
		}
	};

	function getChart() {
		ctx = document.getElementById('myChart').getContext('2d');
		myChart = new Chart(ctx, config);
	}
	function updateChart() {
		myChart.data.datasets.data = newData;
		myChart.update();
	}
</script>

<canvas id="myChart" width="1" height="1" />
