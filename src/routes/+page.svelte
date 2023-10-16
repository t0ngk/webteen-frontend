<script>
	import BestSellerReader from '$lib/components/book/BestSellerReader.svelte';
	import Recommend from '$lib/components/book/Recommend.svelte';
	import Carousel from '$lib/components/home/Carousel.svelte';
	import Ranking from '$lib/components/home/Ranking.svelte';
	import Icon from '@iconify/svelte';
	import { fade } from 'svelte/transition';
</script>

<div class="h-full w-full">
	<!-- carousel -->
	<Carousel />
	<h1 class="text-lg font-semibold py-5 p-3">Recommend for you</h1>
	<div class="w-full flex justify-center">
		<div class="flex flex-row gap-3">
			<Recommend />
		</div>
	</div>
	<div class="w-full flex justify-center p-3">
		<Ranking />
	</div>
	<h1 class="text-lg font-semibold pl-5 py-3">Best Seller</h1>
	<div class="pl-3">
		<BestSellerReader />
	</div>
</div>
