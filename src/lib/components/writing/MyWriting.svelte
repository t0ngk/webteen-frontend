<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';
	import Popup from '../Popup.svelte';
	import AddWritingContent from './popupContent/AddWritingContent.svelte';
	import { goto } from '$app/navigation';
	import { bookStore } from '../../../stores/myStore';

	import { onMount } from 'svelte';
	import axios from 'axios';

	let books = [];
	let isDataLoaded = false;

	let userId = 'b862595f-3ff3-420e-9ec6-fc65d7547059';
	const getBooks = async () => {
		try {
			const res = await axios.get(`http://localhost:8082/book-service/getBookByUserId/${userId}`);
			books = res.data;
			isDataLoaded = true;
			console.log(books);
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
	onMount(getBooks);

	let isPopupOpen = false;
	export let isCreator = true;
</script>

{#if isCreator}
	<div class="container p-2 relative">
		<div class="flex justify-center">
			<h1 class="text-[20px] font-semibold mt-[40px] mb-[20px]">Manage Writing</h1>
		</div>
		<div class="mt-5">
			<div class="flex justify-end">
				<Button
					class="w-auto px-2 py-[3px] rounded-[5px] bg-[#F7B155] flex items-center gap-1"
					on:click={() => {
						isPopupOpen = true;
					}}
				>
					<Icon icon="ic:round-plus" color="black" class="rotate-180" />
					<p class="text-black text-[10px] font-medium">Add Writing</p>
				</Button>
			</div>
			<table class="grid grid-rows-7 mt-5">
				<thead class="">
					<tr
						class="text-[10px] font-medium p-2 border-y-[1px] border-[#D9D9D9] flex items-center justify-between"
					>
						<th class="w-[100px] flex justify-start">Name</th>
						<th class="w-10">Type</th>
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
					{#each books as book}
						<tr
							class="flex items-center justify-between p-2 py-3 text-[8px] border-b-[1px] border-[#ffffff5d]"
						>
							<td class="w-[100px] flex items-center">
								<Button
									class="p-0"
									on:click={() => {
										bookStore.set(book);
										goto(`/manageWriting`);
									}}
								>
									<img
										src={book.cover}
										alt=""
										class="rounded-[5px] w-[36px] h-[36px] object-cover"
									/>
									<p class="text-[8px] font-medium ml-2">{book.title}</p>
								</Button>
							</td>
							<td class="w-10 flex justify-center">
								<p>{book.type}</p>
							</td>
							<td class="w-5 flex justify-center">
								<p>{book.view}K</p>
							</td>
							<td class="w-5 flex justify-center">
								<p>{book.like}</p>
							</td>
							<td class="w-5 flex justify-center">
								<p>{book.comment}</p>
							</td>
							<td class="w-8 flex justify-center">
								<Button class="border-[1px] py-[2px] px-[3px] rounded-[2px]" on:click={() => {}}>
									<Icon icon="mingcute:pencil-fill" color="white" style="font-size: 10px" />
								</Button>
							</td>
							<td class="w-8 flex justify-center">
								<span
									class={`border-[1px] py-[2px] px-[6px] rounded-[2px] ${
										book.status === 'public' || book.status === 'private'
											? 'border-[#F7B155] text-[#F7B155]'
											: book.status === 'decline'
											? 'border-[#EB3333] text-[#EB3333]'
											: ''
									}`}
								>
									<p class={`uppercase text-[6px] font-semibold`}>{book.status}</p>
								</span>
							</td>
						</tr>
					{/each}
				</tbody>
			</table>
		</div>

		<Popup bind:isPopupOpen title={'New Writing'}>
			<AddWritingContent />
		</Popup>
	</div>
{:else}
	<div class="w-full flex flex-col items-center gap-2 mt-16">
		<h1 class="text-xl">You are not a creator</h1>
		<div class="aspect-square w-[60%]">
			<img class="w-full h-full" src="/creator.png" alt="" srcset="" />
		</div>
		<button
			class="w-[60%] transition px-2 py-1 bg-[#F7B155] text-[#161218] hover:bg-[#e8a64f] active:bg-[#d29547] rounded"
		>
			Upgrade to Creator
		</button>
	</div>
{/if}
