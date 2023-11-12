<script>
	/** @type {import('./$types').PageData} */
	import CommentBook from '$lib/components/book/CommentBook.svelte';
	import Recommend from '$lib/components/book/Recommend.svelte';
	import { page } from '$app/stores';
	import Icon from '@iconify/svelte';
	import { onMount } from 'svelte';
	import axios from 'axios';

	const chapterId = $page.params.chapterId;
	let chapter = {};
	let isDataLoaded = false;

	const getDetailChapter = async () => {
		try {
			console.log('chapterId', chapterId);
			const res = await axios.get(`http://localhost:8082/book-service/getChapterById/${chapterId}`);
			chapter = res.data;
			isDataLoaded = true; // Set the flag to true once data is loaded
			console.log(chapter);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	let comments = [];
	let isDataLoaded1 = false;
	const getComment = async () => {
		try {
			console.log('chapterId', chapterId);
			const res = await axios.get(`http://localhost:8082/comment-service/getComment`);
			comments = res.data;
			isDataLoaded1 = true; // Set the flag to true once data is loaded
			console.log(comments);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	onMount(() => {
		getDetailChapter();
		getComment();
	});
</script>

<div class="w-full h-full">
	<div class="w-full bg-black h-12 flex pl-3 items-center">
		<Icon icon="uiw:menu" color="white" style="font-size: 25px" />
	</div>
	<p>chapterId----{chapterId}</p>
	<div class="w-full h-5/6 bg-gray-300">content</div>
	<!-- bar under contents -->
	<div class="w-full h-10 bg-gray-700 flex items-center pl-3">
		<div class="flex flex-row flex-grow">
			<Icon icon="ph:heart-bold" color="white" style="font-size: 20px" />
			<p style="font-size: 14px" class="ml-1">{chapter.view}</p>
			<Icon icon="gg:comment" color="white" style="font-size: 20px" class="ml-2" />
			<p style="font-size: 14px" class="ml-1">{comments.length}</p>
		</div>
		<div class="flex flex-row items-center">
			<p>#{chapter.number}</p>
			<Icon icon="pajamas:chevron-right" color="white" style="font-size: 35px" />
		</div>
	</div>
	<div class="pl-3">
		<h1 class="text-xl font-medium mt-4">Recommend</h1>
		<div class="flex flex-row gap-1 mt-3">
			<!-- <Recommend /> -->
		</div>
		<!-- comment -->
		<!-- <a href="/category/detailBook/detailEP/commentEP"> -->
		<div class="flex flex-row items-center mt-4">
			<h1 class="text-xl font-medium">Top comment</h1>
			<Icon icon="pajamas:chevron-right" color="white" style="font-size: 30px" class="mt-1" />
		</div>
		<div class="p-3 mt-4">
			{#if isDataLoaded1}
				{#each comments as comment}
					<CommentBook {comment} />
				{/each}
			{:else}
				<p>Loading...</p>
			{/if}
		</div>
		<!-- </a> -->
	</div>
</div>
