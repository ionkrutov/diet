<script>
	let genders = [
		{id: 0, text: "муж"},
		{id: 1, text: "жен"},
	]
	let activities = [
		{id: 0, text: "Сидячий образ жизн", k: 1.2},
		{id: 1, text: "Умеренная активность", k: 1.375},
		{id: 2, text: "Средняя активность", k: 1.55},
		{id: 3, text: "Повышенная активность", k: 1.725},
		{id: 0, text: "Профессиональные занятия спортом", k: 1.9},
	]
	let mass;
	let gender = genders[0];
	let amr;
	let age;
	let activity = activities[0];
	let height;
	

	function checkAge() {
		if (age > 80){
			age = 80
		} else if (age < 13) {
			age = 13
		}	
	}

	function calcCalories() {
		bmr = 10 * mass + 6.25 * height - 5 * age
		if (gender.id === 0) {
			bmr += 5
		} else {
			bmr -= 161
		}
		return  bmr * activity.k
	}

	$: {
		let bmr = 10 * mass + 6.25 * height - 5 * age
		if (gender.id === 0) {
			bmr += 5
		} else {
			bmr -= 161
		}
		amr = Math.floor(bmr * activity.k, 1)
		console.log(mass)
	}

</script>

<h1 align=center>Расчет калорий</h1>
<hr>
<main>
	<div align=center>
		<form class="params">
			<label for="mass">Вес</label>
			<input type=number bind:value={mass} id="mass" placeholder="кг" size="4">
			
			<label for="gender">Пол</label>
			<select id="gender" bind:value={gender}>
				{#each genders as gnd}
				<option value={gnd}>
					{gnd.text}
				</option>
				{/each}
			</select>

			<label for="age">Возраст</label>
			<input id="age" type=number bind:value={age} size="4" min="13" max="80" on:change={checkAge}>

			<label for="height">Рост</label>
			<input id="height" type="number" bind:value={height} min="50" max="270" placeholder="см">

			<label for="activity">Активность</label>
			<select id="activity" bind:value={activity}>
				{#each activities as act}
					<option value={act}>
						{act.text}
					</option>
				{/each}
			</select>
		</form>
		{#if !isNaN(amr) && mass && age && height}
			<h1>Калории = {amr}</h1>
		{/if}
		
		
	</div>
	

</main>

<style>
	main {
		text-align: center;
		font-family:'Courier New', Courier, monospace;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		/* background-image: url("/background_photo.jpg"); */
	}

	h1 {
		color: #414042;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 60;
		margin: 1.5rem;
		font-family:'Courier New', Courier, monospace;
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

	.params {
		text-align: left;	
		width: 500px;
		display: grid;
		grid-template-columns: 20% 70%;
		grid-column-gap: 10px;
	}
</style>