<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
	import { Button } from 'flowbite-svelte';
	import Popup from '../../lib/components/Popup.svelte';
	import NewEpisodeContent from '$lib/components/writing/popupContent/NewEpisodeContent.svelte';
	import { bookStore } from '../../stores/myStore';

	let isPopupOpen = false;
	let book;

	bookStore.subscribe((value) => {
		book = value;
	});

	// console.log(book._id);

	import { onMount } from 'svelte';
	import axios from 'axios';

	let chapters = [];
	let isDataLoaded = false;

	const getChapters = async () => {
		try {
			const res = await axios.get(`http://localhost:8082/book-service/getChapterByBookId/${book._id}`);
			chapters = res.data;
			isDataLoaded = true;
			// console.log(chapters[0]);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
	onMount(getChapters);
</script>

<div class="container p-2 mt-5 relative">
	<div class="flex items-center justify-between">
		<div class="flex gap-3 items-center">
			<button
				on:click={() => {
					goto('/writing');
				}}
			>
				<Icon icon="ion:chevron-back" color="white" class="text-[30px]" />
			</button>
			<p class="text-[20px] font-semibold text-center flex-grow">Manage Writing</p>
		</div>
		<button class="mr-4 text-[14px] font-medium text-[#F7B155]">Edit</button>
	</div>

	<div class="flex flex-col items-center my-8">
		<img class="w-[150px] h-[150px] bg-[#373739] rounded-[10px]" src={book.cover} alt="" />
		<div class="my-4 flex flex-col items-center">
			<h1 class="text-[20px] font-semibold">{book.title}</h1>
			<p class="text-[12px] font-normal">{book.category}, {book.type}</p>
		</div>
		<!-- <p class="text-[14px]">Description</p> -->
	</div>

	<div class="px-2">
		<div class="flex justify-between items-center">
			<p class="text-[12px] font-medium text-[#F7B155]">All Episodes ({chapters.length})</p>
			<Button
				class="w-auto px-2 py-[3px] rounded-[5px] bg-[#F7B155] flex items-center gap-1"
				on:click={() => {
					isPopupOpen = true;
				}}
			>
				<Icon icon="ic:round-plus" color="black" class="rotate-180" />
				<p class="text-black text-[10px] font-medium">Add Episode</p>
			</Button>
		</div>

		<table class="grid grid-rows-7 mt-5">
			<thead class="">
				<tr
					class="text-[10px] font-medium p-2 border-y-[1px] border-[#D9D9D9] flex items-center justify-between"
				>
					<th class="w-[100px] flex justify-start">Episode</th>
					<th class="w-5 flex justify-center"
						><Icon icon="mdi:eye" color="white" style="font-size: 12px" class="" /></th
					>
					<th class="w-5 flex justify-center"
						><Icon icon="mdi:heart" color="white" style="font-size: 12px" class="" /></th
					>
					<th class="w-5 flex justify-center"
						><Icon
							icon="iconamoon:comment-fill"
							color="white"
							style="font-size: 12px"
							class=""
						/></th
					>
					<th class="w-8">Edit</th>
					<th class="w-8">Status</th>
				</tr>
			</thead>
			<tbody>
				{#each chapters as episode}
					<tr
						class="flex items-center justify-between p-2 py-3 text-[8px] border-b-[1px] border-[#ffffff5d]"
					>
						<td class="w-[100px] flex items-center">
							<Button
								class="p-0"
								on:click={() => {
									goto(`/displayManga?${episode.title}`);
								}}
							>
								<img
									src={episode.cover}
									alt=""
									class="rounded-[5px] w-[36px] h-[36px] object-cover"
								/>
								<p class="text-[8px] font-medium ml-2">{episode.number} {episode.title}</p>
							</Button>
						</td>
						<td class="w-5 flex justify-center">
							<p>{episode.view}K</p>
						</td>
						<td class="w-5 flex justify-center">
							<p>{episode.like}</p>
						</td>
						<td class="w-5 flex justify-center">
							<p>{episode.comment}</p>
						</td>
						<td class="w-8 flex justify-center">
							<Button class="border-[1px] py-[2px] px-[3px] rounded-[2px]" on:click={() => {}}>
								<Icon icon="mingcute:pencil-fill" color="white" style="font-size: 10px" />
							</Button>
						</td>
						<td class="w-8 flex justify-center">
							<span
								class={`border-[1px] py-[2px] px-[6px] rounded-[2px] ${
									episode.status === 'public' || episode.status === 'private'
										? 'border-[#F7B155] text-[#F7B155]'
										: episode.status === 'decline'
										? 'border-[#EB3333] text-[#EB3333]'
										: ''
								}`}
							>
								<p class={`uppercase text-[6px] font-semibold`}>{episode.status}</p>
							</span>
						</td>
					</tr>
				{/each}
			</tbody>
		</table>
	</div>

	<Popup bind:isPopupOpen title={'New Episode'}>
		<NewEpisodeContent />
	</Popup>
</div>
