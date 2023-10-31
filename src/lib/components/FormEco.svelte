<script>
	import { goto } from '$app/navigation';
	import { cars, energies } from '../../data';

    let formData = {
        carValue: "",
        energyValue: "",
        km: 0,
        year: 0
    }

    const handleSubmit = () => {
        goto('/result')
    }
</script>

<h1 class="text-xl mb-4">Remplisser ce formulaire pour connaître votre impact écologique</h1>
	<form method="POST" action="/result">
		<label for="" class="mb-4">
			Type de voiture
			<select name="car" id="" class="select" required>
				<option value="">Sélectionner une voiture</option>
				{#each cars as car}
					<option value={car.value}>{car.title}</option>
				{/each}
			</select>
		</label>
		<label for="" class="mb-4">
			Energie
			<select name="energy" id="" class="select" required>
				<option value="">Sélectionner un type d'énergie</option>
				{#each energies as energy}
					<option value={energy.value}>{energy.title}</option>
				{/each}
			</select>
		</label>
		<label for="" class="label mb-4">
			Kilométrage
			<input type="number" class="input" required name="km"/>
		</label>
		<label for="" class="label mb-4">
			Année
			<input type="number" class="input" min="1900" max="2023" required name="year"/>
		</label>

		<label for="" class="label mb-8">
			Nombre de passagers
			<select name="passengers" id="" class="select">
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