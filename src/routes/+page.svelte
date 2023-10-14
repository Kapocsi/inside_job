
<script>
	import CssRest from './reset.css.svelte';
</script>

<CssRest />




<style>
.mapSize{
	height: 700px;
	width: 85%;
	float: right;
	
}
</style>

<img class=mapSize src="/map.svg" alt="map" >

<map name="workmap">
	<area shape="rect" coords="34,44,270,350" alt="map1" href="static/map.svg">
	<area shape="rect" coords="290,172,333,250" alt="map2" href="static/map1.svg">
	<area shape="circle" coords="337,300,44" alt="map2" href="static/map2.svg">
	<area shape="circle" coords="337,300,44" alt="map2" href="static/park.svg">
  </map>