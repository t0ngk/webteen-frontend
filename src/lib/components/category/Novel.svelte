<script>
	import BestSellerReader from '../book/BestSellerReader.svelte';
	import Recommend from '../book/Recommend.svelte';
	import { onMount } from 'svelte';
	import axios from 'axios';

	let RecommendBooks = [];
	let isDataLoaded = false;

	const getBooks = async () => {
		try {
			const res = await axios.get(`http://localhost:8082/ranking-service/getRecommendBook/Novel`);
			RecommendBooks = res.data;
			isDataLoaded = true; // Set the flag to true once data is loaded
			console.log(RecommendBooks);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
	onMount(getBooks);
</script>

<div class="h-full w-full p-2">
	<h1 class="text-xl font-medium mt-2">Recommended</h1>
	<div class="flex flex-row gap-3 mt-3">
		{#if isDataLoaded}
			<!-- Render the Recommend component when data is loaded -->
			<Recommend bind:RecommendBooks />
		{:else}
			<!-- Optionally, you can display a loading message or spinner -->
			<p>Loading...</p>
		{/if}
	</div>
	<h1 class="text-xl font-medium mt-2">All Comic</h1>
	<div class="w-full">
		{#if isDataLoaded}
			<!-- Render the Recommend component when data is loaded -->
			<BestSellerReader bind:RecommendBooks />
		{:else}
			<!-- Optionally, you can display a loading message or spinner -->
			<p>Loading...</p>
		{/if}
	</div>
</div>
