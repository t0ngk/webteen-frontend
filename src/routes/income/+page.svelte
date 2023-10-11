<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
	import IncomeTab from '$lib/components/writing/Income/IncomeTab.svelte';
</script>

<div class="h-full w-full ">
	<div class="p-2 mt-2 flex items-center">
		<button
			on:click={() => {
				goto("/writing");
			}}
		>
			<Icon icon="ion:chevron-back" color="white" 
				class="text-[30px] absolute top-4"
			/>
		</button>
		<p class="text-xl font-semibold text-center flex-grow">
			Income
		</p>
	</div>

	<div class="flex w-full h-24 my-3 bg-[#373739] items-center justify-between">
		<div class="flex flex-row">
			<Icon icon="solar:dollar-minimalistic-bold" color="#f7b155" class="ml-8 text-[35px]" />
			<p class="flex text-2xl font-semibold text-[#F7B155] ml-2">800</p>
		</div>
		<button
			on:click={() => {
				goto("/writing");
			}}
			class="w-24 h-9 mr-10 rounded-lg bg-[#F7B155] text-black font-semibold items-center justify-center"
		>
			<p class="text-md">Withdraw</p>
		</button>	
	</div>
	<IncomeTab/>
</div>