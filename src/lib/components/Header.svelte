<script>
	import MyWriting from './writing/MyWriting.svelte';
	import Analysis from './writing/Analysis.svelte';
	import Dashboard from './writing/Dashboard.svelte';
	import Comic from './category/Comic.svelte';
	import Manga from './category/Manga.svelte';
	import Novel from './category/Novel.svelte';
	import { page } from '$app/stores';

	let nav = $page.url.pathname;

	const navWriting = [
		{
			name: 'My Writing',
			component: MyWriting
		},
		{
			name: 'Analysis',
			component: Analysis
		},
		{
			name: 'Dashboard',
			component: Dashboard
		}
	];

	const navCategory = [
		{
			name: 'Comic',
			component: Comic
		},
		{
			name: 'Manga',
			component: Manga
		},
		{
			name: 'Novel',
			component: Novel
		}
	];

	let active = nav === '/writing' ? navWriting[0] : navCategory[0];
</script>

<div>
	<div class="sticky top-0 pt-4 bg-[#161218] z-50">
		<div class="p-2 realtive">
			<h1 class="text-2xl font-semibold tracking-[1px]">
				{nav == '/writing' ? 'WRITING' : 'CATEGORY'}
			</h1>
		</div>
		<div class="flex flex-row justify-between border-b-[1px] border-[#373739a8] px-2">
			{#each nav === '/writing' ? navWriting : navCategory as item}
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
	</div>
	<svelte:component this={active.component} />
</div>
