<script>
	import Search from '$lib/components/admin/Search.svelte';
	import Summary from '$lib/components/admin/Summary.svelte';
	import Chart from '$lib/components/admin/Chart.svelte';
</script>
<div class="h-full w-full p-2 py-4 px-4">
	<Search/>
	<p class="text-3xl">Welcome, Admin!</p>
	<Chart/>
	<Summary/>
</div>