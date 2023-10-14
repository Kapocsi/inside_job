<script>
	// @ts-nocheck

	export let SmallVenue;

	let venues = [
		{
			title: 'Music Venue',
			location: '1111 9 Ave SW',
			description: 'This is the first sample venue description.'
		},
		{
			title: 'Comedy Venue',
			location: '2222 10 Ave SW',
			description: 'This is the second sample venue description.'
		},
		{
			title: 'Dancing Venue',
			location: '3333 11 Ave SW',
			description: 'This is the third sample venue description.'
		}
	];

	/**
	 * @param {{ title?: string; location?: string; description?: string; selected?: any; }} venue
	 */
	function handleEventClick(venue) {
		venue.selected = !venue.selected;
	}
</script>

{#each venues as venue (venue.title)}
	<div class="venue {venue.selected ? 'selected' : ''}" on:click={() => handleEventClick(venue)}>
		<h3>{venue.title}</h3>
		<p>Location: {venue.location}</p>
		<p>Description: {venue.description}</p>
	</div>
{/each}

<style>
	.venue {
		cursor: pointer;
		border: 1px solid #ccc;
		padding: 10px;
		margin: 10px;
		border-radius: 5px;
		background-color: #f0f0f0;
		transition: background-color 0.2s;
		max-width: 20%;
	}

	.venue:hover {
		background-color: #e0e0e0;
	}

	.venue.selected {
		background-color: #fff;
		transform: scale(1.1);
		z-index: 1;
	}
</style>
