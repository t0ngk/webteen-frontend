<script>
	import BestSellerReader from '../book/BestSellerReader.svelte';
	import Recommend from '../book/Recommend.svelte';
</script>

<div class="h-full w-full p-2">
	<h1 class="text-xl font-medium mt-2">Recommended</h1>
	<div class="flex flex-row gap-3 mt-3">
		<Recommend />
	</div>
	<h1 class="text-xl font-medium mt-2">All Comic</h1>
	<div class="w-full">
		<BestSellerReader />
	</div>
</div>
