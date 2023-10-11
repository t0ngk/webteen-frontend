<script>
    import Icon from '@iconify/svelte';

    const bookExamples = [
        {
            type: 'Mystery',
			name: 'No Name 404',
            earn: 1200,
            date: '12/03/2016',
            chapter: 105,
            view: 1234,
            like: 20000,
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU',
		},
		{
			type: 'Comedy',
			name: 'อ่านฉันสิ',
            earn: 999,
            date: '10/09/2023',
            chapter: 40,
            view: 5000,
            like: 1900,
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU',
		},
		{
			type: 'Action',
			name: 'กระต่ายกับเต่า',
            earn: 41,
            date: '09/12/2020',
            chapter: 9,
            view: 300,
            like: 567,
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
		{
            type: 'Mystery',
			name: 'No Name 404',
            earn: 1200,
            date: '12/03/2016',
            chapter: 105,
            view: 1234,
            like: 20000,
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU',
		},
		{
			type: 'Comedy',
			name: 'อ่านฉันสิ',
            earn: 999,
            date: '10/09/2023',
            chapter: 40,
            view: 5000,
            like: 1900,
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU',
		},
		{
			type: 'Action',
			name: 'กระต่ายกับเต่า',
            earn: 41,
            date: '09/12/2020',
            chapter: 9,
            view: 300,
            like: 567,
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
	];
</script>
  
{#each bookExamples as book}
    <div class="flex flex-row p-2 py-3 bg-transparent">
        <div class="flex flex-wrap justify-center max-h-2">
            <img src={book.image} alt="" 
            class="rounded-[10%] w-28 h-28 object-cover"/> 
        </div>
        <div class=" pl-5 flex flex-col justify-center w-auto">
            <p class="text-xs text-[#818181] mb-1">
                {book.type}
            </p>
            <div class="text-white text-md font-bold ">{book.name}</div>
            <div class="flex flec-row">
                <p class="text-[#F7B155] text-sm font-bold my-1">Earn {book.earn}</p>
                <Icon icon="solar:dollar-minimalistic-bold" color="#f7b155" class="mt-1.5 ml-1"/>
            </div>
            <p class="text-[#818181] text-xs mb-1">{book.date}</p>
            <div class="flex flex-col">
                <div class="flex">
                    <div class="flex">
                        <Icon icon="tabler:list" color="#818181" class="mt-[2%] mr-1 text-[15px]"/>
                        <p class="text-[#818181] text-xs">{book.chapter}</p>
                    </div>
                    <div class="flex ml-2">
                        <Icon icon="mdi:eye" color="#818181" class="mt-[4%] mr-1 text-[13px]"/>
                        <p class="text-[#818181] text-xs">{book.view >= 1000 ? (book.view /1000) + 'K' : book.view}</p>
                    </div>
                    <div class="flex ml-2">
                        <Icon icon="ph:heart-bold" color="#818181" class="mt-[5%] mr-1 text-[14px]"/>
                        <p class="text-[#818181] text-xs">{book.like >= 1000 ? (book.like /1000) + 'K' : book.like}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
{/each}