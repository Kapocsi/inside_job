

<script>
    let events = [
      {
        title: 'Sample Event 1',
        date: '2023-10-13',
        description: 'This is the first sample event description.',
        focused: false
      },
      {
        title: 'Sample Event 2',
        date: '2023-10-14',
        description: 'This is the second sample event description.',
        focused: false
      },
      {
        title: 'Sample Event 3',
        date: '2023-10-15',
        description: 'This is the third sample event description.',
        focused: false,
      } ]
  
    /**
	 * @param {{ title: string; date: string; description: string; }} events
	 */
    function handleEventClick(events) {
      // You can add logic to handle the click for the specific event here
    }



  </script>
  
  {#each events as event (event.title)}
    
    {#if event.focused}
    <div class="bigEvent" on:click={() => handleEventClick(event)}>
        <h3>{event.title}</h3>
        <p>Date: {event.date}</p>
        <p>Description: {event.description}</p>
        </div>
    {:else}
    <div class="event" on:click={() => handleEventClick(event)}>
    <h3>{event.title}</h3>
    <p>Date: {event.date}</p>
    <p>Description: {event.description}</p>
    </div>
    {/if}

  {/each}
  
  <style>
    .event {
      cursor: pointer;
      border: 1px solid #ccc;
      padding: 10px;
      margin: 10px;
      border-radius: 5px;
      background-color: #f0f0f0;
      transition: background-color 0.2s;
      max-width: 20%;
    }
    
    .event:hover {
      background-color: #e0e0e0;
    }

    .bigEvent{
      cursor: pointer;
      border: 1px solid #ccc;
      padding: 10px;
      margin: 10px;
      border-radius: 5px;
      background-color: #f0f0f0;
      transition: background-color 0.2s;
      max-width: 60%;
    }
    
  </style>
