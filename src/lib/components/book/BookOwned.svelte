<script>
	// Import your Image component
	// import Image from '../category/assets/person.png';
	import Icon from '@iconify/svelte';

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
		},		
		
	];
</script>

{#each bookExamples as book}

<div class="h-48 w-1/3 justify-center items-center">
	<div class="h-ful w-28 bg-white rounded-lg">
        <div class="bg-[#dfdcdc] w-28 h-28 rounded-lg"></div>
		<div class="ml-1">
			<p class=" text-gray-300 mt-2 text-xs">{book.type}</p>
			<p class="text-[12px] text-black font-medium">{book.name}</p>
		</div>
		
		<div class="flex flex-row justify-end mr-2 mt-1">
			<Icon icon="ph:heart-fill" color="#d01716"/> 
			<p class="text-black text-xs ml-1 mt-[-1px]">{book.like}</p>
		</div>
		<!-- <img src={book.image} alt="" class="rounded-lg w-28 h-28 object-cover" /> -->
	</div>
</div>
	<!-- <div class="bg-white w-1/3 h-48 rounded-lg mb-3 justify-center items-center">
        <div class="justify-center items-center">
            <div class="bg-[#dfdcdc] w-28 h-28 rounded-lg mt-1 ml-[4px]"></div>
        </div>
        <div class="ml-1">
            <p class="text-[#979797] text-xs font-medium">{book.type}</p>
            <h2 class="text-black text-xs mt-[-2px] font-semibold">{book.name}</h2>
            <div class="flex flex-row justify-end mr-2 mt-1">
               <Icon icon="ph:heart-fill" color="#d01716"/> 
               <p class="text-black text-xs ml-1 mt-[-1px]">{book.like}</p>
            </div>
            
        </div>
    </div> -->

	<!-- <div class="w-full h-80 p-1 rounded">
		<div class="w-[100px] h-[50%] bg-white"></div>
		<div class="">text</div>
	</div> -->




    
{/each}
