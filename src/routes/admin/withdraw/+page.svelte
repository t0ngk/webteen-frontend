<!-- YourParentComponent.svelte -->
<script>
	import Search from '$lib/components/admin/Search.svelte';
	import Detailwithdraw from '$lib/components/admin/Detailwithdraw.svelte';
	import Dropdonwall from '$lib/components/admin/Dropdonwall.svelte';
</script>

<div class="h-full w-full p-2">
	<Search />
	<h1 class="text-2xl font-bold text-center mt-5 mb-5">Withdraw</h1>
	<div class="mb-5">
		<Dropdonwall/>
	</div>
	<div class="">
		<Detailwithdraw />
	</div>
</div>
