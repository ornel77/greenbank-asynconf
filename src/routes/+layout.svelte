<script lang="ts">
	import '../app.postcss';
	import { AppBar, AppShell } from '@skeletonlabs/skeleton';
	import { LightSwitch } from '@skeletonlabs/skeleton';
</script>

<AppShell>
	<svelte:fragment slot="header">
		<AppBar class="mb-9 flex">
			<div class="flex w-full justify-between gap-6">

				<h3 class="text-left">Greenbank</h3>
				<LightSwitch class=""/>
			</div>
		</AppBar>
	</svelte:fragment>
	<slot />
</AppShell>
