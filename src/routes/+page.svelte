<script>
	import BestSellerReader from '$lib/components/book/BestSellerReader.svelte';
	import Recommend from '$lib/components/book/Recommend.svelte';
	import Carousel from '$lib/components/home/Carousel.svelte';
	import Ranking from '$lib/components/home/Ranking.svelte';
	import Icon from '@iconify/svelte';
	import { fade } from 'svelte/transition';

	import { onMount } from 'svelte';
	import axios from 'axios';

	let RecommendBooks = [];
	let isDataLoaded = false;

	const getBooks = async () => {
		try {
			const res = await axios.get('http://localhost:8082/book-service/getBook');
			RecommendBooks = res.data;
			isDataLoaded = true; // Set the flag to true once data is loaded
			console.log(RecommendBooks);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	onMount(getBooks);
</script>

<div class="h-full w-full">
	<!-- carousel -->
	<Carousel />
	<h1 class="text-lg font-semibold py-5 p-3">Recommend for you</h1>

	<div class="w-full flex">
		<div class="flex flex-row gap-3 ml-5">
			{#if isDataLoaded}
				<!-- Render the Recommend component when data is loaded -->
				<Recommend bind:RecommendBooks />
			{:else}
				<!-- Optionally, you can display a loading message or spinner -->
				<p>Loading...</p>
			{/if}
		</div>
	</div>
	<div class="w-full flex justify-center p-3">
		<Ranking />
	</div>
	<h1 class="text-lg font-semibold pl-5 py-3">Best Seller</h1>
	<div class="pl-3">
		{#if isDataLoaded}
			<BestSellerReader bind:RecommendBooks />
		{:else}
			<p>Loading...</p>
		{/if}
	</div>
</div>
