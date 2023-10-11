<script>
	import HeaderProfile from '$lib/components/profile/headerProfile.svelte';
	import Icon from '@iconify/svelte';
	// import walletLinear from '@iconify/icons-solar/wallet-linear';
</script>

<div class="h-full w-full p-2">
	<div class="flex pl-3 pt-3 justify-between pr-3">
		<div class="flex flex-row">
			<div class="h-[43px] w-[43px] rounded-full border-solid border-[2.5px] border-amber-300"></div>
			<div class="pl-3">
				<p class="flex">
					<b>username</b>
					<Icon icon="mdi:pencil-outline" color="white" class="h-[25px] w-[25px] pl-2 " />
				</p>
				<p>Level : Royal</p>
			</div>
		</div>
		<div class="flex flex-row items-center">
			<Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
			<h3 class="pl-1"><b>9999</b></h3>
		</div>
		
	</div>
	<div class="h-[115px]">
		<HeaderProfile />
	</div>
</div>
