<script>
    import CreatorPost from './creatorPost.svelte';
    import CreatorWritten from './creatorWritten.svelte';
    import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';

    const myCoinNav = [
		{
			name: 'Post',
			component: CreatorPost
		},
		{
			name: 'My Written',
			component: CreatorWritten
		}
	];

	let active = myCoinNav[0];
</script>

<div class="mt-8">
	<div class="flex flex-row justify-between px-20">
		{#each myCoinNav as item}
			<div>
				<button
					on:click={() => {
						active = item;
					}}
					class={`rounded-xl px-4 text-base font-medium ${
						active == item ? 'border-[#F7B155] bg-[#F7B155] text-slate-950' : 'border-b-[0px] text-[#979797]'
					}`}>{item.name}</button>
			</div>
		{/each}
	</div>
	<svelte:component this={active.component} />
</div>

