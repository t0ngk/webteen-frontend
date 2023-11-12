<script>
	import HeaderProfile from '$lib/components/profile/headerProfile.svelte';
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';
	import { goto } from '$app/navigation';
	// import walletLinear from '@iconify/icons-solar/wallet-linear';

	import axios from 'axios';
	import { onMount } from 'svelte';

	let userData = {}

	const findUser = async () => {

        try {
            const res = await axios.get('http://localhost:8082/user-service/getUsers/b862595f-3ff3-420e-9ec6-fc65d7547059') // ใส่ id ตรงนี้
			userData = res.data
            console.log('Find User Successfully: ', userData);
        } catch (error) {
            console.error('Fail to Find User:', error);
		}
    };

	onMount(findUser);
</script>

<div class="h-full w-full p-2">
	<div class="flex pl-3 pt-3 justify-between pr-3">
		<div class="flex flex-row">
			<div class="h-[43px] w-[43px] rounded-full border-solid border-[2.5px] border-amber-300"></div>
			<div class="pl-3">
				<p class="flex">
					<b>{userData.username}</b>
					<Button class="px-2" on:click={() => {
						goto("/editProfile");
					}}>
					<Icon icon="mdi:pencil-outline" color="white" class="h-[22px] w-[22px] hover:bg-amber-300" />
					</Button>
				</p>
				<p>Level : Royal</p>
			</div>
		</div>
		<Button class="flex flex-row items-center" 
			on:click={() => {
			goto("/myCoin");
		}}
		>
			<Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
			<h3 class="pl-1"><b>9999</b></h3>
		</Button>
		
	</div>
	<div class="h-[115px]">
		<HeaderProfile />
	</div>
</div>
