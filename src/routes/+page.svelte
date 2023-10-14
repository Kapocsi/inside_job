<script>
	import { json } from '@sveltejs/kit';
	import CssRest from './reset.css.svelte';

	function handleRectangleClick(arg0) {
		throw new Error('Function not implemented.');
	}
</script>

<CssRest />

<style>


area {
  border: 2px solid red;
}

img {
  z-index: -1;
}

body {
  	
	position:relative;
	overflow: hidden;
	width:900px;
	height: 700px;
	border: 1px solid black;
	float: right;
}

#container {
  
  grid-gap: 10px;
  height: 100px;
	
}

#container:hover {
  cursor: pointer;
}

.rectangle {
  background-color: #3498db;
  opacity: 0.7;
  border: 1px solid #2980b9;
  position: absolute;
  

}
.road
{
  background-color: black;
  
  position: absolute;

}

.rectangle:hover {
  cursor: pointer;
}

</style>

<body>
	<div class="rectangle" style="left: 50px; top: 100px; width: 150px; height: 80px" on:click={() => handleRectangleClick(1)}></div>
	<div class="rectangle" style="left: 200px; top: 50px; width: 100px; height: 120px" on:click={() => handleRectangleClick(2)}></div>
	<div class="rectangle" style="left: 350px; top: 130px; width: 80px; height: 60px" on:click={() => handleRectangleClick(3)}></div>
	<div class="rectangle" style="left: 580px; top: 400px; width: 120px; height: 150px" on:click={() => handleRectangleClick(4)}></div>
	<div class="rectangle" style="left: 100px; top: 250px; width: 90px; height: 70px" on:click={() => handleRectangleClick(5)}></div>
	<div class="rectangle" style="left: 280px; top: 450px; width: 110px; height: 90px" on:click={() => handleRectangleClick(6)}></div>
	<div class= "rectangle" style="left: 400px; top: 350px; width: 130px; height: 110px" on:click={() => handleRectangleClick(7)}></div>
	<div class="rectangle" style="left: 580px; top: 50px; width: 70px; height: 50px" on:click={() => handleRectangleClick(8)}></div>
	<div class="rectangle" style="left: 580px; top: 270px; width: 140px; height: 120px" on:click={() => handleRectangleClick(9)}></div>
	<div class="road" style="left: 0px; top: 200px; width: 1000px; height: 20px"></div>
	<div class="road" style="left: 0px; top: 240px; width: 1000px; height: 20px"></div>
	<div class="road" id=circle style="left: 210px; top: 240px; width: 25px; height: 1000px"></div>
	
	<div class="road" id=circle style="left: 540px; top: 240px; width: 25px; height: 1000px"></div>
	<div class="road" id=circle style="left: 540px; top: px; width: 25px; height: 1000px"></div>
</body>
  