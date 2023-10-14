<script>
    export let name;
    export let description;
    export let address;
</script>

<div class="event">
    <h1>{name}</h1>
    <p>{description}</p>
    <p>{address}</p>
</div>

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

</style>
