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

	// console.log(book);

	const episodeExamples = [
		{
			name: 'EP1',
			comment: 500,
			view: 1234,
			like: 2000,
			status: 'public',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU'
		},
		{
			name: 'EP2',
			comment: 100,
			view: 5000,
			like: 1900,
			status: 'decline',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU'
		},
		{
			name: 'EP3',
			comment: 50,
			view: 300,
			like: 567,
			status: 'waiting',
			image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg'
		}
	];
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
		<img class="w-[150px] h-[150px] bg-[#373739] rounded-[10px]" src="" alt="" />
		<div class="my-4 flex flex-col items-center">
			<h1 class="text-[20px] font-semibold">{book.name}</h1>
			<p class="text-[12px] font-normal">{book.type}, Penname</p>
		</div>
		<!-- <p class="text-[14px]">Description</p> -->
	</div>

	<div class="px-2">
		<div class="flex justify-between items-center">
			<p class="text-[12px] font-medium text-[#F7B155]">All Episodes ({episodeExamples.length})</p>
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
				{#each episodeExamples as episode}
					<tr
						class="flex items-center justify-between p-2 py-3 text-[8px] border-b-[1px] border-[#ffffff5d]"
					>
						<td class="w-[100px] flex items-center">
							<Button
								class="p-0"
								on:click={() => {
									goto(`/displayManga?${episode.name}`);
								}}
							>
								<img
									src={episode.image}
									alt=""
									class="rounded-[5px] w-[36px] h-[36px] object-cover"
								/>
								<p class="text-[8px] font-medium ml-2">{episode.name}</p>
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
