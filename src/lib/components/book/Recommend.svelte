<script>
	// Import your Image component
	import Image from '../../../assets/person.png';
	import Icon from '@iconify/svelte';
	import Episode from './Episode.svelte';
	import { Button } from 'flowbite-svelte';
	export let RecommendBooks;

	// console.log('recommend', RecommendBooks);
</script>

{#each RecommendBooks as book}
	<div class="h-48 w-1/3">
		<a href="/category/detailBook/{book.bookId}">
			<div class="h-28 w-28 bg-gray-200 rounded-lg">
				<img src={book.cover} alt="" class="rounded-lg w-28 h-28 object-cover" />
			</div>
			<p class=" text-gray-300 mt-2" style="font-size: 9px">{book.type}</p>
			<p class="text-xs font-medium">{book.title}</p>
			<div class="flex flex-row mt-1">
				<img src={Image} class="h-2 w-2 rounded-full mt-0.5" alt="penname" />
				<p class=" text-gray-400 ml-1" style="font-size: 9px">maimee</p>
			</div>
			<div class="flex flex-row items-center">
				<!-- <Icon icon="tabler:list" color="#818181" style="font-size: 11px" class="mt-[2%] mr-1" />
			<p class=" text-gray-400 mt-1" style="font-size: 9px">{book.chapter}</p> -->
				<Icon icon="mdi:eye" color="#818181" style="font-size: 11px" class="mt-[4%] mr-1" />
				<p class=" text-gray-400 mt-1" style="font-size: 9px">{book.view} k</p>
				<Icon
					icon="ph:heart-bold"
					color="#818181"
					style="font-size: 11px"
					class="mt-[5%] mr-1 ml-1"
				/>
				<p class=" text-gray-400 mt-1" style="font-size: 9px">{book.like} k</p>
			</div>
		</a>
	</div>
{/each}
