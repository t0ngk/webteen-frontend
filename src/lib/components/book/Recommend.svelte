<script>
	// Import your Image component
	import Image from '../category/assets/person.png';
	import Icon from '@iconify/svelte';
	import Episode from './Episode.svelte';
	import { Button } from 'flowbite-svelte';

	const bookExamples = [
		{
			type: 'Mystery',
			name: 'Magic Book Shop',
			earn: 1200,
			date: '12/03/2016',
			chapter: 105,
			view: 1234,
			like: 20000,
			writer: 'numnim',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU'
		},
		{
			type: 'Comedy',
			name: 'Love me',
			earn: 999,
			date: '10/09/2023',
			chapter: 40,
			view: 5000,
			like: 1900,
			writer: 'chommy',
			image:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU'
		},
		{
			type: 'Action',
			name: 'กระต่ายกับเต่า',
			earn: 41,
			date: '09/12/2020',
			chapter: 9,
			view: 300,
			like: 567,
			writer: 'lungling',
			image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg'
		}
	];
</script>

{#each bookExamples as book}
	<div class="h-48 w-1/3">
		<a href="/category/detailBook">
			<div class="h-28 w-28 bg-gray-200 rounded-lg">
				<img src={book.image} alt="" class="rounded-lg w-28 h-28 object-cover" />
			</div>
			<p class=" text-gray-300 mt-2" style="font-size: 9px">{book.type}</p>
			<p class="text-xs font-medium">{book.name}</p>
			<div class="flex flex-row mt-1">
				<img src={Image} class="h-2 w-2 rounded-full mt-0.5" alt="penname" />
				<p class=" text-gray-400 ml-1" style="font-size: 9px">{book.writer}</p>
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
