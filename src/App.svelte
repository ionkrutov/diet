<script>
	// export let name;
	let mass ;
</script>

<main>
	<h1>Расчет калорий</h1>
	<hr>
	<label>Вес
		<input bind:value={mass} placeholder="введите вес">
	</label>

</main>

<style>
	main {
		text-align: left;
		font-family:'Courier New', Courier, monospace;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #414042;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 60;
		margin: 1.5rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	:global(html) {
		background-color:#E6E7E8;
	}

	hr {
		color: #D1D3D4;
		margin: 1.5rem;
	}
</style>