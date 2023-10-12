<script>
    import Icon from '@iconify/svelte';
    import { Button } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
    import CreatorProfileNav from './creatorProfileNav.svelte';
</script>

<div class="h-full w-full p-2">
    <div class="p-2 mt-2 flex items-center">
		<button
			on:click={() => {
				// goto("/");
			}}
		>
			<Icon icon="ion:chevron-back" color="white" 
				class="text-[30px] absolute top-4"
			/>
		</button>
	</div>

    <div class="flex flex-col items-center">
        <div class="items-center flex flex-col">
            <div class="h-[110px] w-[110px] rounded-full border-solid border-[3px] border-amber-300 bg-white"></div>
            <p class="text-lg mt-2"><b>Username</b></p>
        </div>
        <div class="flex justify-between w-48 mt-3">
            <div class="items-center flex flex-col">
                <p><b>20</b></p>
                <p>Writing</p>
            </div>
            <div class="items-center flex flex-col">
                <p><b>100k</b></p>
                <p>Follower</p>
            </div>
            <div class="items-center flex flex-col">
                <p><b>22m</b></p>
                <p>Read</p>
            </div>
        </div>
        <Button class="px-10 py-[2px] border-[2px] border-white bg-[#D9D9D9] mt-4">
            <p class="text-slate-950"><b>Follow</b></p>
        </Button>
        <CreatorProfileNav />
    </div>
</div>