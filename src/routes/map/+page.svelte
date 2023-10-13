<script>
    import { onMount } from 'svelte';
    const Leaflet = import('leaflet');
    let map;

    onMount(async () => {
        const L = await Leaflet;
        map = L.map('map').setView([51.505, -0.09], 13);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors'
        }).addTo(map);
    });



</script>

<div id="map">test</div>