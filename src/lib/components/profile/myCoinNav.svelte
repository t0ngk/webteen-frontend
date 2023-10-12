<script>
	import PayMent from './payMentSection.svelte';
    import Icon from '@iconify/svelte';
	import TopUp from './topUpSection.svelte';
	import PayMents from './payMentSection.svelte';
	import { goto } from '$app/navigation';

    const myCoinNav = [
		{
			name: 'Top-Up',
			component: TopUp
		},
		{
			name: 'Payment',
			component: PayMents
		}
	];

	let active = myCoinNav[0];
</script>

<div>
	<div class="p-2 mt-2 flex items-center">
		<button
			on:click={() => {
				goto("/profile");
			}}
		>
			<Icon icon="ion:chevron-back" color="white" 
				class="text-[30px] absolute top-4"
			/>
		</button>
		<p class="text-lg font-semibold text-center flex-grow">
			My Coin
		</p>
	</div>
	<div class="p-2 flex justify-between mt-2 mb-2">
		<div class="flex items-center">
			<Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
			<p class="pl-3 text-lg"><b>9,999</b></p>
		</div>
		<div>
			<Icon icon="ic:baseline-plus" color="white" class="h-[30px] w-[30px]" />
		</div>
	</div>
	<div class="flex flex-row justify-between border-b-[1px] border-[#373739a8] px-10">
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

