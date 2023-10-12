<script>
    import Icon from '@iconify/svelte';

    const bookExamples = [
		{
			name: 'No Name 404',
            author: 'A',
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU',
		},
		{
			name: 'อ่านฉันสิ',
            author: 'B',
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU',
		},
		{
			name: 'กระต่ายกับเต่า',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
		{
			name: 'กระต่ายกับเต่า',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
		{
			name: 'กระต่ายกับเต่า2',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
		{
			name: 'กระต่ายกับเต่า3',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
	];
</script>

<div class="mt-5">
    {#each bookExamples as book}
        <div>
            <div class="bg-[#161218] flex border-b-[0.5px] border-gray-400 h-[85px]">
                <div class="w-[100px] bg-[#D9D9D9]"></div>
                <div class="flex justify-between items-center w-full pr-1">
                    <div class="items-center pl-5 justify-start">
                        <p class="text-base"><b>{book.name}</b></p>
                        <p class="text-base">Author</p>
                    </div>
                    <div class="justify-end">
                        <p class="text-base">#37</p>
                    </div>
                </div>
            </div>
        </div>
    {/each}
</div>