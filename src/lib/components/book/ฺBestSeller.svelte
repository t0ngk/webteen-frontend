<script>
    import Icon from '@iconify/svelte';

    const bookExamples = [
		{
            type: 'Mystery',
			name: 'No Name 404',
            earn: 1200,
            date: '12/03/2023',
            chapter: 105,
            view: 1234,
            like: 20000,
		},
		{
			type: 'Comedy',
			name: 'อ่านฉันสิ',
            earn: 999,
            date: '12/03/2023',
            chapter: 40,
            view: 5000,
            like: 1900,
		},
		{
			type: 'Action',
			name: 'กระต่ายกับเต่า',
            earn: 41,
            date: '12/03/2023',
            chapter: 9,
            view: 300,
            like: 567,
		}
	];
</script>
  
{#each bookExamples as book}
    <div class="flex flex-row p-2 bg-transparent">
        <div class="flex flex-wrap justify-center max-h-2">
            <img src="https://tailwindcss.com/img/card-left.jpg" alt="" 
            class="rounded-[10%] w-28 h-28 object-cover"/> 
        </div>
        <div class=" pl-5 flex flex-col justify-center w-auto">
            <p class="text-xs text-[#818181] mb-1">
                {book.type}
            </p>
            <div class="text-white text-md font-bold ">{book.name}</div>
            <p class="text-[#F7B155] text-sm font-bold my-1">Earn {book.earn}</p>
            <p class="text-[#818181] text-xs mb-1">{book.date}</p>
            <div class="flex flex-col mr-10">
                <div class="flex">
                    <div class="flex">
                        <Icon icon="tabler:list" color="#818181" style="font-size: 15px" class="mt-[2%] mr-1"/>
                        <p class="text-[#818181] text-xs">{book.chapter}</p>
                    </div>
                    <div class="flex ml-2">
                        <Icon icon="mdi:eye" color="#818181" style="font-size: 13px" class="mt-[8%] mr-1"/>
                        <p class="text-[#818181] text-xs">{book.view >= 1000 ? (book.view /1000) + 'K' : book.view}</p>
                    </div>
                    <div class="flex ml-2">
                        <Icon icon="ph:heart-bold" color="#818181" style="font-size: 14px" class="mt-[5%] mr-1"/>
                        <p class="text-[#818181] text-xs">{book.like >= 1000 ? (book.like /1000) + 'K' : book.like}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
{/each}