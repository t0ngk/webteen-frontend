<script>
	import Header from '$lib/components/Header.svelte';
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
</script>

<div class=" h-full w-full px-2">
	<div class="h-[115px] justify-between">
		<Header />
		<button
			on:click={() => {
				goto("/income");
			}}
			class="absolute w-10 h-10 right-0 top-0"
		>
			<div class="absolute w-10 h-10 bg-[#373739] rounded-full right-4 top-4"
			/>
			<Icon icon="la:wallet" color="#f7b155" class="absolute right-6 top-6 text-[24px]"/>
		</button>
	</div>
</div>
