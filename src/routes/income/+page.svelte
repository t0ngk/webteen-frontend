<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
	import IncomeTab from '$lib/components/writing/Income/IncomeTab.svelte';
	import Popup from '$lib/components/Popup.svelte';
	import WithdrawPopup from '$lib/components/writing/Income/WithdrawPopup.svelte';

	let isPopupOpen = false;
	let coin = 800
</script>

<div class="h-full w-full">
	<div class="sticky top-0 bg-[#161218]">
		<div class="p-2 flex items-center">
			<button
				on:click={() => {
					goto("/writing");
				}}
			>
				<Icon icon="ion:chevron-back" color="white" 
					class="text-[30px] absolute top-3"
				/>
			</button>
			<p class="text-xl font-semibold text-center flex-grow mt-1">
				Income
			</p>
		</div>

		<div class="flex w-full h-24 mt-1.5 bg-[#373739] items-center justify-between">
			<div class="flex flex-row">
				<Icon icon="solar:dollar-minimalistic-bold" color="#f7b155" class="ml-8 text-[35px]" />
				<p class="flex text-2xl font-semibold text-[#F7B155] ml-2">{coin}</p>
			</div>
			<button
				on:click={() => {
					isPopupOpen = true;
				}}
				class="w-24 h-9 mr-8 rounded-lg bg-[#F7B155] text-black font-semibold items-center justify-center"
			>
				<p class="text-md">Withdraw</p>
			</button>	
		</div>
	</div>
	<IncomeTab/>
	<WithdrawPopup bind:isPopupOpen title={'Withdraw'} coin={coin}/>
</div>