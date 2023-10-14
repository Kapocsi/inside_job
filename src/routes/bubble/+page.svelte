<script>
	import Bubble from './bubble.svelte';
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';

	function transformData(jsonData) {
		const transformedData = {};

		jsonData.forEach((item) => {
			const genre = item.Genre;
			const locationName = item.location_name;
			const totalEvents = parseInt(item.number_of_events);
			const totalRating = parseInt(item.avg_ratings_for_location);

			if (!transformedData[genre]) {
				transformedData[genre] = {
					name: genre,
					type: 'packedbubble',
					data: []
				};
			}

			transformedData[genre].data.push({
				name: locationName,
				value: totalEvents,
				labelrank: totalRating
			});
		});

		return Object.values(transformedData);
	}

	// create recent events store
	let recent_events = writable([]);
	onMount(async () => {
		let x = await fetch('http://dns.phantommedia.online:3000/api/bubblechart', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			}
		}).then((t) => t.json());
		recent_events.set(transformData(x));
	});
</script>

<div class="container">
	<div>stuufs</div>
	<dv>
		{#if $recent_events.length > 0}
			<Bubble data={$recent_events} />
		{/if}
	</dv>
</div>

<style>
	.container {
		display: grid;
		grid-template-columns: 1fr 3fr;
		grid-template-rows: 1fr;
	}
</style>
