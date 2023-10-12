<script>
	import Recommend from '../book/Recommend.svelte';
	import BestSeller from '../book/ฺBestSeller.svelte';
</script>

<div class="h-full w-full p-2">
	<h1 class="text-xl font-medium mt-2">Recommended</h1>
	<div class="flex flex-row gap-3 mt-3">
		<Recommend />
	</div>
	<h1 class="text-xl font-medium mt-2">All Manga</h1>
	<div>
		<BestSeller />
	</div>
</div>
