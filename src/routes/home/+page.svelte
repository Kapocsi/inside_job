<script>
	import CssRest from '../reset.css.svelte';
</script>

<div class="container">
	<div class="shadow1" />
	<div class="shadow2" />
	<div class="modal">
		<div class="title">Gather Grid</div>
		<select>
			<option>Demo</option>
		</select>

		<div class="button">
			<button>Go</button>
		</div>
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
		position: relative;
		/* madefrom chat gpt */
		background: linear-gradient(0deg, #f0f0f0 1px, transparent 1px),
			linear-gradient(90deg, #f0f0f0 1px, transparent 1px);
		background-size: 20px 20px;
	}

	.shadow2 {
		position: absolute;
		z-index: -1;
		box-shadow: -150px -50px 200px 200px rgba(80, 180, 200, 0.5);
	}

	.shadow1 {
		position: absolute;
		z-index: -1;
		box-shadow: 150px 50px 200px 200px rgba(30, 43, 200, 0.5);
	}

	.modal select {
		width: 100%;
		height: 25px;
		border-radius: 0.5rem;
	}

	.title {
		font-size: 3rem;
		font-weight: 900;
		padding: 1.5rem 0;
	}

	.button {
		width: 100%;
		padding: 1rem 0;
		display: flex;
	}
	button {
		width: auto;
		height: 2rem;
		padding: 0 1rem;
		margin: auto;
		border-radius: 0.5rem;
		background: #f0f0f0;
		border: none;
		font-size: 1rem;
		cursor: pointer;
	}
</style>
