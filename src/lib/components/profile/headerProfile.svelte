<script>
	// Page
	import Recent from './Recent.svelte';
	import Favorite from './Favorite.svelte';
	import Owend from './Owend.svelte';
	import Creator from './Creator.svelte';
	import { page } from '$app/stores';

	let nav = $page.url.pathname;

	const navProfile = [
		{
			name: 'Recent',
			component: Recent
		},
		{
			name: 'Favorite',
			component: Favorite
		},
		{
			name: 'Owned',
			component: Owend
		}
	];

	let active = navProfile[0];
</script>

<div>
	<div class="p-2">
		<h1 class="text-2xl font-semibold tracking-[1px]">
		</h1>
	</div>
	<div class="flex flex-row justify-between border-b-[1px] border-[#373739a8] px-2">
		{#each navProfile as item}
			<div>
				<button
					on:click={() => {
						active = item;
					}}
					class={` py-1 px-2 text-base font-medium ${
						active == item ? 'border-[#F7B155] text-[#F7B155] border-b-[2px]' : 'border-b-[0px] text-[#979797]'
					}`}>{item.name}</button
				>
			</div>
		{/each}
	</div>
	<svelte:component this={active.component} />
</div>
