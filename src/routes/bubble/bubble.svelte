<script>
    import { onMount } from 'svelte';
    import Highcharts from 'highcharts';
    
    onMount(() => {
        let chartspace = document.getElementById('chart-container')
        const chart = Highcharts.chart({
            chart: {
                type: 'line',
                renderTo: 'chart-container'
            },
            title: {
                text: 'My Line Chart'
            },
            series: [
    {
        name: 'Data Series',
        type: 'line',
        data: [1, 2, 3, 4, 5],
    
    },
  ],
        });
    }

    );


</script>

<div id="chart-container"></div>

<style>
#chart-container {
  width: 100%;
  height: 400px;
  outline: 1px solid red;
}

</style>