<script>
  let events = [
    {
      title: 'Sample Event 1',
      date: '2023-10-13',
      description: 'This is the first sample event description.',
      focused: false,
    },
    {
      title: 'Sample Event 2',
      date: '2023-10-14',
      description: 'This is the second sample event description.',
      focused: false,
    },
    {
      title: 'Sample Event 3',
      date: '2023-10-15',
      description: 'This is the third sample event description.',
      focused: false,
    }
  ];

  /**
	 * @type {{ title: string; date: string; description: string; focused: boolean; } | null}
	 */
  let clickedEvent = null;

  function handleEventClick(event) {
    clickedEvent = event;
  }
</script>

{#each events as event (event.title)}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div
    class="{event.focused ? 'bigEvent' : 'event'} {clickedEvent === event ? 'enlarged' : ''}"
    on:click={() => handleEventClick(event)}
  >
    <h3>{event.title}</h3>
    <p>Date: {event.date}</p>
    <p>Description: {event.description}</p>
  </div>
{/each}

<style>
  .event, .bigEvent {
    cursor: pointer;
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
    background-color: #f0f0f0;
    transition: background-color 0.2s;
    max-width: 20%;
  }
  
  .event:hover, .bigEvent:hover {
    background-color: #e0e0e0;
  }

  .enlarged {
    transform: scale(2.0); /* Enlarge the event on click */
    z-index: 1; /* Bring the enlarged event to the front */
    margin-top: 10%;
    margin-bottom: 10%;
    margin-left: 15%;
  }
</style>
