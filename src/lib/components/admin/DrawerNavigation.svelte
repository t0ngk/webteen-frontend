<script>
	import { goto } from '$app/navigation';
	import Icon from '@iconify/svelte';
	import windowClose from '@iconify/icons-mdi/window-close';
	import { fade, fly } from 'svelte/transition';

	const drawers = [
		{
			name: 'Home',
			icon: 'fluent:home-16-regular',
			path: '/admin'
		},
		{
			name: 'Written',
			icon: 'fluent:note-edit-20-regular',
			path: '/admin/writtenview'
		},
		{
			name: 'Report',
			icon: 'octicon:report-24',
			path: '/admin/report'
		},
		{
			name: 'Withdraw',
			icon: 'uil:money-withdrawal',
			path: '/admin/FilteredData'
		},
		{
			name: 'Writer',
			icon: 'fluent:notepad-person-24-regular',
			path: '/admin/writer'
		}
	];

	export let open = true;
</script>

{#if open}
	<button
		class="fixed inset-0 z-50 bg-black/50 cursor-default"
		on:click={() => {
			open = false;
		}}
		transition:fade={{ duration: 150 }}
	/>
	<div
		class="absolute top-0 left-0 z-50 h-[100dvh] bg-[#292932] w-full max-w-[350px] shadow-lg p-6"
		transition:fly={{
			x: -350,
			duration: 300,
			opacity: 1
		}}
	>
		<div class="flex justify-between mb-6">
			<div>
				<p class="text-2xl">Manage</p>
			</div>
			<button class="text-2xl" on:click={() => (open = false)}><Icon icon={windowClose} /></button>
		</div>
		<div class="flex flex-col gap-2">
			{#each drawers as item}
				<button
					class="w-full p-2 hover:bg-[#1c1c22] rounded text-xl transition"
					on:click={() => {
						goto(item.path);
						open = false;
					}}
				>
					<div class="flex items-center">
						<Icon icon={item.icon} />
						<span class="ml-2">{item.name}</span>
					</div>
				</button>
			{/each}
		</div>
	</div>
{/if}
