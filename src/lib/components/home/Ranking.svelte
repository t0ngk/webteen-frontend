<script>
	// Import your Image component
	import Icon from '@iconify/svelte';
	import Image from '../../../assets/person.png';
	export let typeBook;
	// export let ranked;
	import { onMount } from 'svelte';
	import axios from 'axios';

	let ranked = [];
	let isDataLoaded1 = false;

	const getRank = async () => {
		try {
			const res = await axios.get(`http://localhost:8082/ranking-service/rankBookType/${typeBook}`);
			ranked = res.data;
			isDataLoaded1 = true; // Set the flag to true once data is loaded
			console.log(typeBook, ranked);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};

	onMount(getRank);
</script>

<div class="min-w-full">
	<div class="flex flex-row items-center mb-4">
		<h1 class="text-lg font-semibold flex-grow">{typeBook}</h1>
		<Icon icon="pajamas:chevron-right" color="white" style="font-size: 30px" />
	</div>
	{#each ranked.slice(0, 3) as book, index}
		<a href="/category/detailBook/{book.bookId}">
			<div class="flex flex-row items-center h-16">
				<p class="font-semibold mr-5 ml-3">{index + 1}</p>
				<div class="w-[50px] h-[50px] bg-gray-300 rounded-lg">
					<img src={book.cover} alt="" class="rounded-lg w-full h-full object-cover" />
				</div>
				<div class="ml-3">
					<p class=" text-gray-300" style="font-size: 9px">{book.type}</p>
					<p class="text-xs font-medium mb-1">{book.title}</p>
					<div class="flex flex-row">
						<img src={Image} class="h-2 w-2 rounded-full mt-0.5" alt="penname" />
						<p class=" text-gray-400 ml-1" style="font-size: 9px">mairuu</p>
					</div>
				</div>
			</div>
		</a>
	{/each}
</div>
