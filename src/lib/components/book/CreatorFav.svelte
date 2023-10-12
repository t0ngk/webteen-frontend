<script>
    import Icon from '@iconify/svelte';

    const CreatorFav = [
		{
			creator_name: 'No Name 404',
            author: 'A',
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN-TGUnYCYmr-IVYQjN9DgneizSMZJUob733p-6Vw3ByB9QuSTaLYOSLkvRz9VSw75vQ&usqp=CAU',
		},
		{
			creator_name: '404 Not Found',
            author: 'B',
            image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQn7BZnI7PbKGdUHaL0GkSyNdj530Gvhde3ZdLwxXPF6gWUSefNsxbTl8PElwmNcELou8s&usqp=CAU',
		},
		{
			creator_name: 'Yak mak',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
		{
			creator_name: 'Pocky',
            author: 'C',
            image: 'https://i.pinimg.com/originals/fc/7c/8b/fc7c8bd8f242e2765dfd99b619002712.jpg',
		},
	];
</script>

<div class="mt-5">
    {#each CreatorFav as creator}
        <div>
            <div class="bg-[#161218] flex h-[85px] mb-1 pl-2 items-center">
                <div class="h-14 w-14 bg-white rounded-full"></div>
                <div class="flex justify-between items-center w-full pr-1">
                    <div class="items-center pl-5 justify-start">
                        <p class="text-base"><b>{creator.creator_name}</b></p>
                    </div>
                    <div class="justify-end">
                        <button class="bg-[#F7B155] hover:bg-white text-black font-normal py-2 px-4 rounded">
                            Following
                        </button>
                    </div>
                </div>
            </div>
        </div>
    {/each}
</div>
