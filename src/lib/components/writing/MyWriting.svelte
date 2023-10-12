<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';
	import Popup from '../Popup.svelte';
	import AddWritingContent from './popupContent/AddWritingContent.svelte';

	let isPopupOpen = false;

	const bookExamples = [
		{
			type: 'Mystery',
			name: 'No Name 404',
			comment: 500,
			view: 1234,
			like: 2000,
			status: 'public',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU'
		},
		{
			type: 'Comedy',
			name: 'อ่านฉันสิ',
			comment: 100,
			view: 5000,
			like: 1900,
			status: 'decline',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU'
		},
		{
			type: 'Action',
			name: 'กระต่ายกับเต่า',
			comment: 50,
			view: 300,
			like: 567,
			status: 'waiting',
			image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg'
		}
	];
</script>

<div class="container p-2 relative">
	<div class="flex justify-center">
		<h1 class="text-[20px] font-semibold mt-[40px] mb-[20px]">Manage Writing</h1>
	</div>
	<div class="">
		<div class="flex justify-between">
			<Button class="w-auto px-2 py-[3px] rounded-[5px] bg-white flex items-center gap-1">
				<p class="text-black text-[10px] font-medium">All</p>
				<Icon icon="octicon:triangle-up-16" color="black" class="rotate-180" />
			</Button>
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
				{#each bookExamples as book}
					<tr
						class="flex items-center justify-between p-2 py-3 text-[8px] border-b-[1px] border-[#ffffff5d]"
					>
						<td class="w-[100px] flex items-center">
							<img src={book.image} alt="" class="rounded-[5px] w-[36px] h-[36px] object-cover" />
							<p class="text-[8px] font-medium ml-2">{book.name}</p>
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
