<script>
	import Header from '$lib/components/Header.svelte';
	import Icon from '@iconify/svelte';
</script>

<div class="h-full w-full p-2 py-4">
	<div class="w-10 h-10 bg-[#373739] rounded-full right-4 top-4"
		style="position: absolute; "
	/>
	<Icon icon="la:wallet" color="#f7b155" 
		style="position: absolute; font-size: 24;"
		class="right-6 top-6"
	/>
	<div class="h-[115px]">
		<Header />
	</div>
</div>
