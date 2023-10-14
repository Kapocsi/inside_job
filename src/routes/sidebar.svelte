<script>
	import { API_URL } from '$lib';
	import { onMount } from 'svelte';
    import { writable } from 'svelte/store';
	import Event from './event.svelte';

    // create recent events store 
    let recent_events = writable([]);
    onMount(async () => {
        let x = await fetch(API_URL + '/api/db', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({
				query: 'SELECT * FROM "Event" e INNER JOIN "Location" l on e."LocationID" = l.Id'
			})
		})
        .then((t) => t.json());
        recent_events.set(x);
    });

</script>

{console.log($recent_events)}

<div>
	<h1>Upcoming Events</h1>
    {#each $recent_events as re}
       <Event name={re.Name} description={re.Description} address={re.Address} /> 
    {/each}


</div>
