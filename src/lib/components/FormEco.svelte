<script>
	import { cars, energies } from '../../data';

	let carValue = '';
	let energyValue = '';
	let km = 0;
	let year = 0;
	let passengers = 0;
	let kmNote = 0;
	let yearNote = 0;

	let score = 0;

	let total = 0;

	let borrowingRate = 0
	let bonus = 0

	let recap = {score, borrowingRate, bonus, total}

	function calculateTotal() {
		if (km < 30000 && km >= 25000) {
			kmNote = 0.1;
		} else if (km >= 20000) {
			kmNote = 0.3;
		} else if (km >= 15000) {
			kmNote = 0.5;
		} else if (km >= 10000) {
			kmNote = 0.7;
		} else if (km >= 5000) {
			kmNote = 0.9;
		}

		if (year >= 2010) {
			yearNote = 0.7;
		} else if (year >= 2000) {
			yearNote = 0.5;
		} else if (year >= 1990) {
			yearNote = 0.4;
		} else if (year >= 1980) {
			yearNote = 0.3;
		} else if (year >= 1970) {
			yearNote = 0.2;
		} else if (year >= 1960) {
			yearNote = 0.1;
		} else if (year <= 0) {
			yearNote = 0;
		}

		score = Math.round((parseFloat(carValue) + parseFloat(energyValue) + yearNote + kmNote) * 10);

		if(score <= 40 && score >= 34) {
			borrowingRate = 1.85
		} else if(score >= 26) {
			borrowingRate = 2.1
		} else if(score >= 16) {
			borrowingRate = 2.52
		} else if(score >= 11) {
			borrowingRate = 2.74
		} else if(score >= 0) {
			borrowingRate = 3
		}

		switch (Number(passengers)) {
			case 1:
				bonus = .11
				break;
			case 2:
				bonus = -.17
				break;
			case 3:
				bonus = -.29
				break;
			case 4:
				bonus = -.53
				break;
		
			default:
				break;
		}
		total = borrowingRate + bonus

		recap = {score, borrowingRate, bonus, total}

		return recap;
	}

	// $: total = carValue + energyValue + kmNote + yearNote + Number(passengers);
</script>

<h1 class="text-xl mb-4">Remplisser ce formulaire pour connaître votre impact écologique</h1>
<form action="" on:submit|preventDefault={calculateTotal}>
	<label for="" class="mb-4">
		Type de voiture
		<select name="car" id="" class="select" bind:value={carValue} required>
			<option value="">Sélectionner une voiture</option>
			{#each cars as car}
				<option value={car.value}>{car.title}</option>
			{/each}
		</select>
	</label>
	<label for="" class="mb-4">
		Energie
		<select name="energy" id="" class="select" bind:value={energyValue} required>
			<option value="">Sélectionner un type d'énergie</option>
			{#each energies as energy}
				<option value={energy.value}>{energy.title}</option>
			{/each}
		</select>
	</label>
	<label for="" class="label mb-4">
		Kilométrage (entre 5000 et 30000km)
		<input type="number" class="input" bind:value={km} required name="km" />
	</label>
	<label for="" class="label mb-4">
		Année (à partir de 1960)
		<input
			type="number"
			class="input"
			min="1900"
			max="2023"
			required
			name="year"
			bind:value={year}
		/>
	</label>

	<label for="" class="label mb-8">
		Nombre de passagers
		<select name="passengers" id="" class="select" bind:value={passengers}>
			<option value="1">1 Passager</option>
			<option value="2">2 Passagers</option>
			<option value="3">3 Passagers</option>
			<option value="4">4 Passagers</option>
		</select>
	</label>
	<div class="flex justify-center">
		<button type="submit" class="btn btn-sm variant-filled-primary w-56">Envoyer</button>
	</div>
</form>

<div class="card mt-10">
	<header class="card-header">
		<h2>Récapitulatif</h2>
	</header>
	<section class="p-4">
		<p>Score {recap.score} / 40</p>
		<p>Taux d'emprunt : {recap.borrowingRate}</p>
		<p>Nombre de passagers : {passengers}</p>
		<p>Bonus/Malus : {recap.bonus}%</p>

		<div class="mt-5">
			<h3>{recap.total} % de frais pour l'achat de cette voiture</h3>
		</div>
	</section>
</div>