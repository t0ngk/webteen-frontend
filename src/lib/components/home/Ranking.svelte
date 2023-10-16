<script>
	// Import your Image component
	import Icon from '@iconify/svelte';
	import Image from '../../../assets/person.png';

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

<div class="w-full">
	<div class="flex flex-row items-center mb-4">
		<h1 class="text-lg font-semibold flex-grow">Comic Ranking</h1>
		<Icon icon="pajamas:chevron-right" color="white" style="font-size: 30px" />
	</div>
	{#each bookExamples as book, index}
		<div class="flex flex-row items-center h-16">
			<p class="font-semibold mr-5 ml-3">{index + 1}</p>
			<div class="w-[50px] h-[50px] bg-gray-300 rounded-lg" />
			<div class="ml-3">
				<p class=" text-gray-300" style="font-size: 9px">{book.type}</p>
				<p class="text-xs font-medium mb-1">{book.name}</p>
				<div class="flex flex-row">
					<img src={Image} class="h-2 w-2 rounded-full mt-0.5" alt="penname" />
					<p class=" text-gray-400 ml-1" style="font-size: 9px">{book.writer}</p>
				</div>
			</div>
		</div>
	{/each}
</div>
