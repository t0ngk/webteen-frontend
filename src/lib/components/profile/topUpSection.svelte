<script>
	import Icon from "@iconify/svelte";
	import { onMount } from "svelte";
  let coinHistory = [];
	onMount(async () => {
		const req = await fetch('http://localhost:8082/statement-service/statement', {
			method: 'GET',
			headers: {
				'Content-Type': 'application/json',
				Authorization: `Bearer ${localStorage.getItem('accessToken')}`
			}
		});
		if (req.ok) {
			const stan = await req.json();
			console.log(stan);
			coinHistory = stan;
		}
	})


</script>

<div class="h-full w-full p-2 pt-5">
    {#each coinHistory as item}
        <div class="flex border-b-[1px] border-[#373739] py-3 items-center">
            <div>
                <Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
            </div>
            <div class="pl-3">
                <p class="mb-1"><b>{item.amount}</b></p>
                <div class="flex items-center">
                    <p class="text-xs">{new Date(item.createdAt).toLocaleString()}</p>
                    <!-- <p class="pl-2 text-xs">{item.time}</p> -->
                </div>
            </div>
        </div>
    {/each}
</div>
