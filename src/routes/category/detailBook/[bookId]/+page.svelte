<script>
	/** @type {import('./$types').PageData} */
	import Episode from '$lib/components/book/Episode.svelte';
	import Icon from '@iconify/svelte';
	import { page } from '$app/stores';
	import { onMount } from 'svelte';
	import axios from 'axios';

	const bookId = $page.params.bookId;
	let Book = {};
	let isDataLoaded = false;

	const getDetailBooks = async () => {
		try {
			console.log('bookId', bookId);
			const res = await axios.get(`http://localhost:8082/book-service/getBookById/${bookId}`);
			Book = res.data;
			isDataLoaded = true; // Set the flag to true once data is loaded
			// console.log(Book);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	let chapters = [];
	let isDataLoaded1 = false;

	const getChapter = async () => {
		try {
			const res = await axios.get(
				`http://localhost:8082/book-service/getChapterByBookId/${bookId}`
			);
			chapters = res.data;
			isDataLoaded1 = true; // Set the flag to true once data is loaded
			console.log('hiiii chappter', chapters);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	onMount(() => {
		getDetailBooks();
		getChapter();
	});
</script>

<div class="h-full w-full">
	<div class="sticky top-0">
		<div class="bg-black w-full h-72 p-3 bg-opacity-40 absolute">
			<div class="flex justify-between w-full mt-3">
				<Icon icon="pajamas:chevron-left" color="white" style="font-size: 35px" />
				<Icon icon="ph:heart-bold" color="white" style="font-size: 23px" />
			</div>

			<div class="pl-3 w-5/6">
				<p class="text-sm text-gray-200 mt-7">{Book.type}</p>
				<p class="text-xl font-medium">{Book.title}</p>
				<p class="line-clamp-4 text-sm">
					{Book.description}
				</p>
			</div>
		</div>
		<img src={Book.cover} alt="" class="w-full h-72 object-cover" />
	</div>
	<!-- <div class="divide-y divide-white"> -->
	{#if isDataLoaded1}
		{#each chapters as chapter}
			<Episode {chapter} {bookId} />
		{/each}
	{:else}
		<p>Loading...</p>
	{/if}

	<!-- </div> -->
</div>
