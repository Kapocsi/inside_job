<script>
	import Bubble from './bubble.svelte';
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';
	import Event from "./event.svelte"
	import CssReset from "../reset.css.svelte"



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

	// Careful these are passed by reference down to the components
	let bubble_selected = writable('');

	let data = writable({
		"genre": [],
		"location": []
	});

	bubble_selected.subscribe(() => {
		refresh_sidebar();
	});

	async function refresh_sidebar(type) {
		if ($bubble_selected === '') {
			console.log("No bubble selected")
			return;
		}

		$data["location"] = await fetch('http://dns.phantommedia.online:3000/api/location', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			}, body: JSON.stringify({ query: $bubble_selected.name })
		}).then((t) => t.json());

		
		$data["genre"] = await fetch('http://dns.phantommedia.online:3000/api/genre', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			}, body: JSON.stringify({ query:$bubble_selected.series.name })
		}).then((t) => t.json());

		console.log($data);

	}

	onMount(async () => {
		await refresh_sidebar();
	});

</script>

<CssReset/>

<div class="container">
	<div>
		<h1>Similar Events</h1>
		{#each $data["genre"] as item}
			<Event title={item.EventName} description={item.Description} />
		{/each}
		<h1>Happening Nearby</h1>
		{#each $data["genre"] as item}
			<Event title={item.EventName} description={item.Description} />
		{/each}
	</div>
	<dv>
		{#if $recent_events.length > 0}
			<Bubble data={$recent_events} selected={bubble_selected} />
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
