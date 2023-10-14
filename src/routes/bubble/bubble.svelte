<script>
	export let data;
	import { onMount } from 'svelte';
	import * as Highcharts from 'highcharts';
	import HighchartsMore from 'highcharts/highcharts-more';
	import HighchartsExporting from 'highcharts/modules/exporting';
	import HighchartsAccessibility from 'highcharts/modules/accessibility';

	onMount(() => {
		console.log(data);
		HighchartsMore(Highcharts);
		HighchartsExporting(Highcharts);
		HighchartsAccessibility(Highcharts);
		let chart = Highcharts.chart({
			chart: {
				type: 'packedbubble',
				renderTo: 'chart-container'
			},
			title: {
				text: 'Average Ratings for Locations by Genre',
				align: 'center'
			},
			tooltip: {
				useHTML: true,
				pointFormat:
					'<b>{point.name}:</b> {point.value} events and {point.labelrank} average rating'
			},
			plotOptions: {
				packedbubble: {
					events: {
						click: function (event) {
							console.log(event.point);
						}
					},
					minSize: '30%',
					maxSize: '120%',
					layoutAlgorithm: {
						splitSeries: false,
						gravitationalConstant: 0.02
					},
					dataLabels: {
						enabled: true,
						format: '{point.name}',
						filter: {
							property: 'y',
							operator: '>',
							value: 1
						},
						style: {
							color: 'black',
							textOutline: 'none',
							fontWeight: 'normal'
						}
					}
				}
			},
			series: data
		});
	});
</script>

<div class="container">
	<div id="chart-container" />
</div>

<style>
	.container {
		border: 1px solid #000;
	}
	#chart-container {
		height: 100dvh;
	}
</style>
