<script>
	import PayMent from './payMentSection.svelte';
	import Icon from '@iconify/svelte';
	import TopUp from './topUpSection.svelte';
	import PayMents from './payMentSection.svelte';
	import { goto } from '$app/navigation';
	import { fade, fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	const myCoinNav = [
		{
			name: 'Top-Up',
			component: TopUp
		},
		{
			name: 'Payment',
			component: PayMents
		}
	];

	let active = myCoinNav[0];

	let toggleTopUp = false;
	let baht = 0;
	let total = 0;
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
			total = stan.reduce((acc, cur) => {
				if (cur.type == 'COIN') {
					return acc + cur.amount;
				} else {
					return acc - cur.amount;
				}
			}, 0);
		}
	})

	const topup = async () => {
		const req = await fetch('http://localhost:8082/statement-service/statement', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json',
				Authorization: `Bearer ${localStorage.getItem('accessToken')}`
			},
			body: JSON.stringify({
				price: baht,
				status: 'APPROVE',
				type: 'COIN',
				amount: baht * 4
			})
		});
		if (req.ok) {
			alert('Top up success');
			window.location.reload();
		} else {
			alert('Top up failed');
		}
	};
</script>

{#if toggleTopUp}
	<div
		class="w-full h-1/2 absolute bottom-0 left-0 rounded z-50 shadow-xl bg-[#1c1a1e] flex flex-col p-4 gap-2"
		transition:fly={{ y: 500, opacity: 1, duration: 500 }}
	>
		<div>
			<p class="text-lg font-semibold">Top Up</p>
			<p class="text-sm">Enter the amount you want to top up</p>
		</div>
		<div class="w-full">
			<p>Thai Baht</p>
			<input type="number" bind:value={baht} class="rounded-xl w-full text-black" />
		</div>
		<div class="w-full">
			<p>Coin</p>
			<input disabled type="number" value={baht * 4} class="rounded-xl w-full text-black" />
		</div>
		<button class="w-full py-2 p-1 bg-[#d78d2d] rounded-xl" on:click={() => topup()}>Top up</button>
		<button
			on:click={() => {
				toggleTopUp = false;
				baht = 0;
			}}
			class="w-full py-2 p-1 bg-red-600 rounded-xl">Cancel</button
		>
	</div>
	<button
		transition:fade
		on:click={() => (toggleTopUp = false)}
		class="inset-0 w-full h-full absolute bg-black/30 z-40"
	/>
{/if}

<div>
	<div class="p-2 mt-2 flex items-center">
		<button
			on:click={() => {
				goto('/profile');
			}}
		>
			<Icon icon="ion:chevron-back" color="white" class="text-[30px] absolute top-4" />
		</button>
		<p class="text-lg font-semibold text-center flex-grow">My Coin</p>
	</div>
	<div class="p-2 flex justify-between mt-2 mb-2">
		<div class="flex items-center">
			<Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
			<p class="pl-3 text-lg"><b>{total}</b></p>
		</div>
		<button on:click={() => (toggleTopUp = true)}>
			<Icon icon="ic:baseline-plus" color="white" class="h-[30px] w-[30px]" />
		</button>
	</div>
	<div class="flex flex-row justify-between border-b-[1px] border-[#373739a8] px-10">
		{#each myCoinNav as item}
			<div>
				<button
					on:click={() => {
						active = item;
					}}
					class={` py-1 px-2 text-base font-medium ${
						active == item
							? 'border-[#F7B155] text-[#F7B155] border-b-[2px]'
							: 'border-b-[0px] text-[#979797]'
					}`}>{item.name}</button
				>
			</div>
		{/each}
	</div>
	<svelte:component this={active.component} />
</div>
