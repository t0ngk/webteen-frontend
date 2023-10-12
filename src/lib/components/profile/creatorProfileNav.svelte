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
	<div class="flex flex-row justify-between border-b-[1px] border-[#373739a8] px-20">
		{#each myCoinNav as item}
			<div>
				<button
					on:click={() => {
						active = item;
					}}
					class={` py-1 px-2 text-base font-medium ${
						active == item ? 'border-[#F7B155] text-[#F7B155] border-b-[2px]' : 'border-b-[0px] text-[#979797]'
					}`}>{item.name}</button>
			</div>
		{/each}
	</div>
	<svelte:component this={active.component} />
</div>

