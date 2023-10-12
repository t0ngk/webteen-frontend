<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
	import { Button } from 'flowbite-svelte';
</script>

<div class="h-full w-full justify-items-center">
	<div class="p-2 mt-2 flex items-center">
		<button
			on:click={() => {
				goto('/profile');
			}}
		>
			<Icon icon="ion:chevron-back" color="white" class="text-[30px] absolute top-4" />
		</button>
		<p class="text-xl font-semibold text-center flex-grow">Edit Profile</p>
		<button class="mr-4 text-lg">Save</button>
	</div>

	<div class="w-full">
		<div class="flex justify-center">
			<div class=" w-[179px] h-[179px] bg-white rounded-full m-3">
				<div class="w-[40px] h-[40px] ml-32 mt-32 rounded-full bg-[#F7B155] flex items-center">
					<Icon icon="mdi:pencil-outline" color="black" class="h-[26px] w-[30px] m-2" />
				</div>
			</div>
		</div>

        <div class="mx-6">
            <p>Display Name</p>
            <div class="flex border-b border-[#979797] py-1 mb-2">
                <input class="appearance-none bg-transparent border-none w-full text-gray-700 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Display Name" aria-label="displayname">
            </div>

            <p>Username</p>
            <div class="flex border-b border-[#979797] py-1 mb-2">
                <input class="appearance-none bg-transparent border-none w-full text-gray-700 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="username" aria-label="username">
            </div>

            <p>Email</p>
            <div class="flex border-b border-[#979797] py-1 mb-2">
                <input class="appearance-none bg-transparent border-none w-full text-gray-700 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="email"aria-label="email">
            </div>

            <p>Password</p>
            <div class="flex border-b border-[#979797] py-1 mb-2">
                <input class="appearance-none bg-transparent border-none w-full text-gray-700 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="*********" aria-label="password">
            </div>
        </div>
	</div>
</div>
