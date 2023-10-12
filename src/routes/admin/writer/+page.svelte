<script>
	import Search from '$lib/components/admin/Search.svelte';
	import Dropdonwall from '$lib/components/admin/Dropdonwall.svelte';
	import Tableapprovewriter from '$lib/components/admin/Tableapprovewriter.svelte';
</script>
<div class="h-full w-full p-2">
	<Search/>
	<h1 class="text-2xl font-bold text-center mt-5 mb-5">Writer</h1>
	<div class="mb-5">
		<Dropdonwall/>
	</div>
	<Tableapprovewriter/>
</div>
