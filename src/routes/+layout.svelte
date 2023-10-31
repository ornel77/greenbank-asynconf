<script lang="ts">
	import '../app.postcss';
	import { AppBar, AppShell } from '@skeletonlabs/skeleton';
	import { LightSwitch } from '@skeletonlabs/skeleton';
</script>

<AppShell>
	<svelte:fragment slot="header">
		<AppBar class="mb-9 flex">
			<div class="flex w-full justify-between items-center gap-8">

				<h3 class="text-left text-2xl uppercase">Greenbank</h3>
				<LightSwitch class=""/>
			</div>
		</AppBar>
	</svelte:fragment>
	<slot />
</AppShell>
