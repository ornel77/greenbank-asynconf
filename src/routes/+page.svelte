<script>
	import { cars, energies } from '../data';
</script>

<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->

<div class="container mx-auto overflow-hidden lg:max-w-[650px] px-4">
	<h1 class="text-xl mb-4">Remplisser ce formulaire pour connaître votre impact écologique</h1>
	<form action="">
		<label for="" class="mb-4">
			Type de voiture
			<select name="" id="" class="select" required>
				<option value="">Sélectionner une voiture</option>
				{#each cars as car}
					<option value={car.id}>{car.title}</option>
				{/each}
			</select>
		</label>
		<label for="" class="mb-4">
			Energie
			<select name="" id="" class="select" required>
				<option value="">Sélectionner un type d'énergie</option>
				{#each energies as energy}
					<option value={energy.id}>{energy.title}</option>
				{/each}
			</select>
		</label>
		<label for="" class="label mb-4">
			Kilométrage
			<input type="number" name="" id="" class="input" required />
		</label>
		<label for="" class="label mb-4">
			Année
			<input type="number" class="input" min="1900" max="2023" required />
		</label>

		<label for="" class="label mb-8">
			Nombre de passagers
			<select name="" id="" class="select">
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
</div>
